# 编译Runtime源码objc4-723

### 1. OS X 10.13 Xcode 9.x 请参考：[objc - 编译Runtime源码objc4-723](https://github.com/qing-song/debug-objc2)

### 2. OS X 10.12 Xcode 8.x 请参考：[objc - 编译Runtime源码objc4-706][objc4-706]

### 3. OS X 10.11 Xcode 7.x 请参考：[objc - 编译Runtime源码objc4-680][objc4-680]

Runtime源码objc4-723编译环境：[macOS 11.13][macOS]、[Xcode 9.3][Xcode]
需要用到的源码：
> * dyld-519.2.1
> * launchd-842.1.4
> * libauto-187
> * Libc-825.40.1
> * libclosure-67
> * libdispatch-913.1.6
> * libpthread-301.1.6
> * xnu-4570.1.46
> * objc4-723

遇到问题可以参考 [objc4-680][objc4-680] 和 [objc4- 706][objc4-706] 的解决方案。

补充：
#### 1. `Use of undeclared identifier ‘DYLD_MACOSX_VERSION_10_11`
`Use of undeclared identifier ‘DYLD_MACOSX_VERSION_10_12`
`Use of undeclared identifier ‘DYLD_MACOSX_VERSION_10_13`
在 dyld_priv.h 文件顶部加入一下宏：
`#define DYLD_MACOSX_VERSION_10_11        0x000A0B00`
`#define DYLD_MACOSX_VERSION_10_12        0x000A0C00`
`#define DYLD_MACOSX_VERSION_10_13        0x000A0D00`

#### 2. `'objc-runtime-oldobjc-shared-cache.h.h' file not found`
这个问题，貌似是苹果官方文档写的问题，引入错误，这里，可以参考旧版本的写法：
注释掉 `// include "objc-runtime-oldobjc-shared-cache.h.h"`
引入 `objc-runtime-old.h`



[objc4-680]:https://blog.csdn.net/wotors/article/details/52489464
[objc4-706]:https://blog.csdn.net/WOTors/article/details/54426316?locationNum=7&fps=1
[macOS]:https://opensource.apple.com/release/macos-1013.html
[Xcode]:https://developer.apple.com/download/more/?q=xcode
