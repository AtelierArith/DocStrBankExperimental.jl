```
J = imdilate(I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}; hsize=3, vsize=3, sel=nothing)::GMTimage
```

Dilate the grayscale or binary image I.

The dilation is performed with a matrix of 0’s and 1’s with width `hsize` and height `vsize`, or, if possible, with the structuring element `sel`. Later case is faster but it is only available for binary images, where by *binary* images we mean Boolean images or images with only 0’s and 1’s of UInt8 type.

### Args

  * `I::Union{GMTimage{<:UInt8, 2}, GMTimage{<:Bool, 2}}`: Input image.

### Kwargs

  * `hsize::Int=3`: Horizontal size of the 'box' structuring element.
  * `vsize::Int=3`: Vertical size of the 'box' structuring element.
  * `sel=nothing`: Structuring element (See $strel$ function). An alternative to `hsize` and `vsize` options. If equal to $nothing$, a structuring box of size `hsize` x `vsize` is used.

### Returns

A new `GMTimage` of the same type as `I` with the dilation applied.

### Example

Dilation with a square of width 3 (the default when neither `sel`, nor `hsize` or `vsize` are specified)

```julia
I = gmtread(TESTSDIR * "assets/fig_text_bw.png");
J = imdilate(I);
grdimage(I, figsize=7)
grdimage!(J, figsize=7, xshift=7.1, show=true)
```
