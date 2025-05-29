```
convert2image(dataset::ImageNet, i)
convert2image(dataset::ImageNet, x)
```

Convert the observation(s) `i` from dataset `d` to image(s). It can also convert a numerical array `x`.

# Examples

```julia-repl
julia> using ImageNetDataset, ImageInTerminal

julia> d = ImageNet()

julia> convert2image(d, 1:2)
# You should see 2 images in the terminal

julia> x = d[1].features;

julia> convert2image(MNIST, x) # or convert2image(d, x)
```
