```
Options(object, filename::AbstractString)
```

ブロードキャスティングに便利な `Options` の追加コンストラクタです。

```jldoctest
julia> objects = [1, 2];

julia> filenames = ["a", "b"];

julia> Options.(objects, filenames)
2-element Vector{Options}:
 Options(1, "a", missing, missing, missing)
 Options(2, "b", missing, missing, missing)
```
