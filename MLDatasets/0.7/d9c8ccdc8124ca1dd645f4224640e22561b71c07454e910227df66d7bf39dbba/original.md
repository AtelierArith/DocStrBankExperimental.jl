```
convert2image(d, i)
convert2image(d, x)
convert2image(DType, x)
```

Convert the observation(s) `i` from dataset `d` to image(s). It can also convert a numerical array `x`.

In order to support a new dataset, e.g. `MyDataset`,  implement `convert2image(::Type{MyDataset}, x::AbstractArray)`.

# Examples

```julia-repl
julia> using MLDatasets, ImageInTerminal

julia> d = MNIST()

julia> convert2image(d, 1:2) 
# You should see 2 images in the terminal

julia> x = d[1].features;

julia> convert2image(MNIST, x) # or convert2image(d, x)
```
