`AGray32` uses a `UInt32` representation of color, 0xAAIIIIII, where I=intensity (grayscale value) and A=alpha. Each II pair is assumed to be the same.  This format is often used by external libraries such as Cairo.

You can extract the single gray value with `gray(c)` and the alpha as `alpha(c)`.  You can construct them directly from a `UInt32`, or as `AGray32(i,alpha)`. Note that `i` and `alpha` are interpreted on a scale from 0 (black) to 1 (white).
