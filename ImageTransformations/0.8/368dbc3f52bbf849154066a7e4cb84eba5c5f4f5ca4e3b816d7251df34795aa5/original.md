```
imresize(img, sz) -> imgr
imresize(img, inds) -> imgr
imresize(img; ratio) -> imgr
```

Change `img` to be of size `sz` (or to have indices `inds`). If `ratio` is used, then `sz = ceil(Int, size(img).*ratio)`. This interpolates the values at sub-pixel locations. If you are shrinking the image, you risk aliasing unless you low-pass filter `img` first.

The keyword `method` takes any InterpolationType from Interpolations.jl or a Degree, which is used to define a BSpline interpolation of that degree, in order to set the interpolation method used in the image resizing.

# Examples

```julia
julia> img = testimage("lena_gray_256") # 256*256
julia> imresize(img, 128, 128) # 128*128
julia> imresize(img, 1:128, 1:128) # 128*128
julia> imresize(img, (128, 128)) # 128*128
julia> imresize(img, (1:128, 1:128)) # 128*128
julia> imresize(img, (1:128, )) # 128*256
julia> imresize(img, 128) # 128*256
julia> imresize(img, ratio = 0.5) #128*128
julia> imresize(img, ratio = (2, 1)) # 256*128
julia> imresize(img, (128,128), method=Linear()) #128*128
julia> imresize(img, (128,128), method=BSpline(Linear())) #128*128
julia> imresize(img, (128,128), method=Lanczos4OpenCV()) #128*128

σ = map((o,n)->0.75*o/n, size(img), sz)
kern = KernelFactors.gaussian(σ)   # from ImageFiltering
imgr = imresize(imfilter(img, kern, NA()), sz)
```

See also [`restrict`](@ref).
