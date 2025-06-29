```
J = imfilter(I::GMTimage, kernel::Matrix{<:Real}; normalize::Int=1, sep::Bool=false)::GMTimage
```

Generic convolution filter.

### Args

  * `I::GMTimage`: Input image. This can be a RGB or grayscale image.
  * `kernel::Matrix{<:Real}`: The filter kernel MxN matrix.

### Kwargs

  * `normalize::Int=1`: Normalize the filter to unit sum. This is the default, unless $sum(kernel) == 0$,  case in which we change it to 0.
  * `sep::Bool=false`: Try to decompose the filter into two 1-D components. If possible, this leads to a faster execution.  MxN x (m+n) operations, instead of MxN x mxn. Where M,N and m,n are the sizes of the image I and the kernel filter respectively.

### Returns

A new `GMTimage` of the same type as `I` with the filtered image.

### Example

Apply an 3x3 Mean Removal filter to the image "moon.png".

```julia
I = gmtread(TESTSDIR * "assets/moon.png");
J = imfilter(I, [-1 -1 -1; -1 9 -1; -1 -1 -1]);
grdimage(I, figsize=5)
grdimage!(J, figsize=5, xshift=5, show=true)
```
