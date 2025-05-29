```
t = region_tree(img, homogeneous)
```

Creates a region tree from `img` by splitting it recursively until all the regions are homogeneous.

```
b = homogeneous(img)
```

Returns true if `img` is homogeneous.

# Examples

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> img = 0.1*rand(6, 6);

julia> img[4:end, 4:end] .+= 10;

julia> function homogeneous(img)
           min, max = extrema(img)
           max - min < 0.2
       end
homogeneous (generic function with 1 method)

julia> t = region_tree(img, homogeneous);
```
