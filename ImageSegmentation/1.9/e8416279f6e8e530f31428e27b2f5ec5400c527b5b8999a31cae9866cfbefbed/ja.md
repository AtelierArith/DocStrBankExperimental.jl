```
seg = region_splitting(img, homogeneous)
```

`img`を再帰的に分割して、すべてのセグメントが均質になるまで分割します。

```
b = homogeneous(img)
```

`img`が均質であればtrueを返します。

# 例

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
