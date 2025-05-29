```
imshow(img; kwargs...)
imshow(img, (minval, maxval); kwargs...)
```

Draw an image, defined by any of the following:

  * A string with a valid file name of an image.
  * A 3-dimensional *H*×*W*×*C* array, which will be drawn as an image *W* pixels wide and *H* pixels high, with *C* channels (3 or 4), corresponding to RGB or RGBA values between 0 and 1.
  * A matrix of values, which will be drawn with a hue corresponding to their relative position in the current colormap. The range of values mapped in the colormap is by default `[0, 1]`, but can be set to an arbitrary range between `minval` and `maxval`. Setting either limit to `nothing` will cause it to be automatically determined based on the data.

# Examples

```julia
# Create an image
x = LinRange(-3, 3, 150)
y = LinRange(-2, 2, 100)
# RGB values
r = (1 .+ cos.(atan.(y, x')))/2
g = (1 .+ sin.(atan.(y, x')))/2
b = exp.(-(x'.^2 .+ y.^2)/4)
data = cat(r, g, b, dims=3)
# Draw the image
imshow(data)

```
