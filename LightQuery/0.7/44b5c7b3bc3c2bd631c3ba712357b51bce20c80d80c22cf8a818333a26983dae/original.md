```
@if_known(something)
```

If `something` is `missing`, return `missing`, otherwise, `something`.

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
