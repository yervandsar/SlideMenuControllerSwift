SlideMenuControllerSwift
========================

[![Platform](http://img.shields.io/badge/platform-iOS-blue.svg?style=flat
)](https://developer.apple.com/iphone/index.action)
[![Language](http://img.shields.io/badge/language-Swift-brightgreen.svg?style=flat
)](https://developer.apple.com/swift)
[![License](http://img.shields.io/badge/license-MIT-lightgrey.svg?style=flat
)](http://mit-license.org)
[![Issues](https://img.shields.io/github/issues/dekatotoro/SlideMenuControllerSwift.svg?style=flat
)](https://github.com/dekatotoro/SlideMenuControllerSwift/issues?state=open)
[![Downloads](https://img.shields.io/cocoapods/dt/SlideMenuControllerSwift.svg)](https://cocoapods.org/pods/SlideMenuControllerSwift)


iOS Slide View based on iQON, Feedly, Google+, Ameba iPhone app.

![sample](Screenshots/SlideMenuControllerSwift3.gif)

## Installation

#### CocoaPods
```
pod 'SlideMenuControllerSwift', :git => 'https://github.com/yervandsar/SlideMenuControllerSwift.git'
```

## Usage

### Setup

Add `import SlideMenuControllerSwift` in your file

In your app delegate:

```swift

func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {

    // create viewController code...

    let slideMenuController = SlideMenuController(mainViewController: mainViewController, leftMenuViewController: leftViewController, rightMenuViewController: rightViewController)
    self.window?.rootViewController = slideMenuController
    self.window?.makeKeyAndVisible()    

    return true
}
```

#### Storyboard Support

1. Inherit `SlideMenuController` and put UIViewController in a storyboard.
2. Override `awakeFromNib`, then instantiate any view controllers

```swift
class ContainerViewController: SlideMenuController {

    override func awakeFromNib() {
        if let controller = self.storyboard?.instantiateViewControllerWithIdentifier("Main") {
            self.mainViewController = controller
        }
        if let controller = self.storyboard?.instantiateViewControllerWithIdentifier("Left") {
            self.leftViewController = controller
        }
        super.awakeFromNib()
    }

}
```

If you want to use the custom option, please set them before calling the init method, like so:

```swift
SlideMenuOptions.leftViewWidth = 50
SlideMenuOptions.contentViewScale = .50
...

```

### You can access from UIViewController

```swift
self.slideMenuController()?
```
or
```swift
if let slideMenuController = self.slideMenuController() {
    // some code
}
```
### add navigationBarButton
```swift
viewController.addLeftBarButtonWithImage(UIImage(named: "hoge")!)
viewController.addRightBarButtonWithImage(UIImage(named: "fuga")!)
```

### open and close
```swift
// Open
self.slideMenuController()?.openLeft()
self.slideMenuController()?.openRight()

// close
self.slideMenuController()?.closeLeft()
self.slideMenuController()?.closeRight()
```

### monitor the states of menu, you can use `SlideMenuControllerDelegate` use this:
```swift
func leftWillOpen()
func leftDidOpen()
func leftWillClose()
func leftDidClose()
func rightWillOpen()
func rightDidOpen()
func rightWillClose()
func rightDidClose()
```

## Requirements
- Swift 5.0
- iOS 9.0

## Features
- Highly customizable
- Complete example


## Contributing
Forks, patches and other feedback are welcome.

## Creators
### SlideMenuControllerSwift
- [Yuji Hato](https://github.com/dekatotoro), [Blog](http://buzzmemo.blogspot.jp/)
- [Yervand Saribekyan](https://www.linkedin.com/in/yersar/)

## License
SlideMenuControllerSwift is available under the MIT license. See the [LICENSE](./LICENSE) file for more info.
