```
scitype(X)
```

`X`の科学的タイプ（解釈）、その機械タイプとは異なる。

### 例

```julia-repl
julia> scitype(3.14)
Continuous

julia> scitype([1, 2, missing])
AbstractVector{Union{Missing, Count}} 

julia> scitype((5, "beige"))
Tuple{Count, Textual}

julia> using CategoricalArrays

julia> X = (gender = categorical(['M', 'M', 'F', 'M', 'F']),
            ndevices = [1, 3, 2, 3, 2]);

julia> scitype(X)
Table{Union{AbstractVector{Count}, AbstractVector{Multiclass{2}}}}
```
