```
I = image_alpha!(img::GMTimage; alpha_ind::Integer, alpha_vec::Vector{Integer}, alpha_band::UInt8, burn=false)
```

Change the alpha transparency of the GMTimage object `img`. If the image is indexed, one can either change just the color index that will be made transparent by using `alpha_ind=n` or provide a vector of transaparency values in the range [0 255]; This vector can be shorter than the orginal number of colors. Use `alpha_band` to change, or add, the alpha of true color images (RGB).

  * `burn`: The background color to be used in the compositing. It can be a 3-tuple of integers in the range [0 255]  or a symbol or string that will a color name. *e.g.*, `bg=:blue`. The default is `:white`. This option  is only usable for true color images and `alpha_band`. Then instead of adding the alpha band, that band is  used to replace or compose (when the alpha_band values are variable to other than 0 or 255) the background color.

### Examples

```jldoctest
# Example1: change to the third color in cmap to represent the new transparent color
julia> image_alpha!(img, alpha_ind=3)

#Example2: change to the first 6 colors in cmap by assigning them random values
julia> image_alpha!(img, alpha_vec=round.(Int32,rand(6).*255))

# Burn the red color in a random image
julia> img = mat2img(rand(UInt8, 750, 750, 3));
julia> mask = rand(Bool, 750, 750);
julia> image_alpha!(img, alpha_band=mask, burn=:red);
```
