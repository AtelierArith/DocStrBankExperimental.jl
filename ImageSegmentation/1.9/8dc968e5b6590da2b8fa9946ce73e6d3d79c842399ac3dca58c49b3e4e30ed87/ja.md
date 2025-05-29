```
t = region_tree(img, homogeneous)
```

`img`から領域ツリーを作成し、すべての領域が均質になるまで再帰的に分割します。

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

julia> t = region_tree(img, homogeneous);
```
