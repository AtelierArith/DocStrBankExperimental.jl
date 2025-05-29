```
平均化
```

要素を平均化するための削減関数。

# 例

```jldoctest
julia> using DataTools
       using Transducers

julia> foldl(平均化, Filter(isodd), 1:10)
5.0

julia> rf = oncol(a = 平均化, b = 平均化);

julia> foldl(rf, Map(identity), [(a = 1, b = 2), (a = 2, b = 3)])
(a = 1.5, b = 2.5)
```
