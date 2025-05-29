```
@if_known(something)
```

`something` が `missing` の場合、`missing` を返し、それ以外の場合は `something` を返します。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> function test(x)
           first(@if_known(x))
       end;


julia> @inferred test((1, 2))
1

julia> @inferred test(missing)
missing
```
