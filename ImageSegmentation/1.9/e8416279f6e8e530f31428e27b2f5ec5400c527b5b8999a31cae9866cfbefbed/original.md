```
seg = region_splitting(img, homogeneous)
```

Segments `img` by recursively splitting it until all the segments are homogeneous.

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

julia> seg = region_splitting(img, homogeneous);
```
