# Media Picker!

Hello! **Media Picker** an Android Library for pick image.

It's very easy to apply to your project.



### Screenshot

<img src="https://user-images.githubusercontent.com/36754680/66700279-c3724a00-ed29-11e9-8604-d2c479ef5f68.png" style="zoom:75%;" />

<br>

### Api Level
```css
defaultConfig {
    minSdkVersion 14
    targetSdkVersion 29
}
```

<br>

### Download

 Add it in your root build.gradle at the end of repositories:

```css
allprojects {
	repositories {
		...
		maven { url 'https://jitpack.io' }
	}
}
```

 Add the dependency

```css
dependencies {
    implementation 'com.github.kimdohun0104:MediaPicker:1.1.0'
}
```

<br>

## Usage

 You can check how to pick images from media_picker_example for actual application

### Simple Start

```kotlin
MediaPicker.createImage(this)		
	.start(REQUEST_CODE)
```

You can start picker activity like this. MediaPicker is both Activity and Fragment are available. 

<br>

### Get Results

```kotlin
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
	super.onActivityResult(requestCode, resultCode, data)
	if (resultCode == Activity.RESULT_OK) {
		if (requestCode == SELECT_IMAGE_CODE) {
			Log.d("RESULT", MediaPicker.getResult(data).toString())
		}
	}
}
```

 You can get results from **onActivityResult** with MediaPicker.getResult(). It will return list of actual path of the images.

<br>

### Get Result with Callback
 It is very simple way to get results.
 ```kotlin
MediaPicker.createImage(this)
   .start { Log.d("DEBUGLOG", it.toString()) }
 ```

<br>

### Single Mode & Limit Number of Select

```kotlin
MediaPicker.createImage(this)
	.single()
	.start(REQUEST_CODE)
```

  Single mode is useful to pick one image. It automatically prevents one or more select.

```kotlin
MediaPicker.createImage(this)
	.maxImageCount(10) 		// can select up to 10
	.start(REQUEST_CODE)
```

<br>

### Custom UI

 You can change toolbar and status bar with simple method

```kotlin
MediaPicker.createImage(this)
	.toolbarTitle("Select Image")
	.toolbarCompleteText("complete")
	.toolbarBackgroundColor(R.color.colorPrimary)
	.toolbarTextColor(R.color.colorWhite)
	.theme(R.style.AppTheme)
	.start(REQUEST_CODE)
```

<br>

### RecyclerView Span

 You can customize span for RecyclerView. You can set portrait and landscape respectively.

```
MediaPicker.createImage(this)
	.portraitSpan(3)
	.landscapeSpan(5)
	.start(REQUEST_CODE)
```

<br>

### Orientation

 Can prevent screen rotate if you want.

```
MediaPicker.createImage(this)
	.orientation(PickerOrientation.PORTRAIT)
	.start(REQUEST_CODE)
```

<br>

### All Settings

```kotlin
MediaPicker.createImage(this)
	.orientation(PickerOrientation.PORTRAIT) // (default by PickerOrientation.BOTH)
	.single()	// single mode for select one image
	.maxImageCount(10)	// limit count (default by 999)
	.toolbarTitle("New title")	// (default by "Select Image")
	.toolbarCompleteText("DONE")	// (default by "Complete")
	.toolbarBackgroundColor(R.color.colorPrimary)
	.toolbarTextColor(R.color.colorPrimaryDark)	// (default by R.color.colorWhite)
	.portraitSpan(4)	// (default by 3)
	.landscapeSpan(6)	// (default by 5)
	.orientation(PickerOrientation.PORTAIT)	// (default by PickerOrientation.BOTH)
	.theme(R.style.AppTheme)
	.permissionRequireText(R.string.permission_require)
	.start(REQUEST_CODE)
```

<br>


<br>



### License

```
MIT License

Copyright (c) 2019 kimdohun0104

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
