`RGB24` uses a `UInt32` representation of color, 0xAARRGGBB, where R=red, G=green, B=blue and A is irrelevant. This format is often used by external libraries such as Cairo.

`RGB24` colors do not have fields named `r`, `g`, `b`, but you can still extract the individual components with `red(c)`, `green(c)`, `blue(c)`.  You can construct them directly from a `UInt32`, or as `RGB(r, g, b)`.
