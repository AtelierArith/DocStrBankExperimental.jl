`ARGB32` uses a `UInt32` representation of color, 0xAARRGGBB, where R=red, G=green, B=blue and A is the alpha channel. This format is often used by external libraries such as Cairo.  On a little-endian machine, this type has the exact same storage format as `BGRA{N0f8}`.

`ARGB32` colors do not have fields named `alpha`, `r`, `g`, `b`, but you can still extract the individual components with `alpha(c)`, `red(c)`, `green(c)`, `blue(c)`.  You can construct them directly from a `UInt32`, or as `ARGB32(r, g, b, alpha)`.
