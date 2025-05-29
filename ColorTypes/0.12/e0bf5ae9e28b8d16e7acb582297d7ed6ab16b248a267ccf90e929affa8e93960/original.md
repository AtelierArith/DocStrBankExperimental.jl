`Gray24` uses a `UInt32` representation of color, 0xAAIIIIII, where I=intensity (grayscale value) and A is irrelevant. Each II pair is assumed to be the same.  This format is often used by external libraries such as Cairo.

You can extract the single gray value with `gray(c)`.  You can construct them directly from a `UInt32`, or as `Gray24(i)`. Note that `i` is interpreted on a scale from 0 (black) to 1 (white).
