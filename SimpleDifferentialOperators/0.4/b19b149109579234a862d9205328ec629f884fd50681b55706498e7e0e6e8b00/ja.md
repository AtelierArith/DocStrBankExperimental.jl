```
interiornodes(x̄, bc)
```

拡張グリッド `x̄` に対して与えられた境界条件 `bc` に対応する内部グリッドを返します。

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 0:5
0:5

julia> interiornodes(x̄, (Reflecting(), Reflecting()))
1:4

julia> x̄ = [1.0; 1.5; 1.7]
3-element Array{Float64,1}:
 1.0
 1.5
 1.7

julia> interiornodes(x̄, (Mixed(1.0), Mixed(1.0)))
1-element Array{Float64,1}:
 1.5
```
