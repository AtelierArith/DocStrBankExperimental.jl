```
DrawImageMask(image)
```

An interactive widget that allows you to draw a mask on top of an image.

# Examples

```julia
# Notebook Cell 1
using WebToys, FileIO
my_image = load("./path/to/image.png")
mask_widget = DrawImageMask(my_image)

# Notebook Cell 2
# Draw on top of the image in the notebook output before running this cell.
masked_image = my_image .* getmask(mask_widget)
```
