```
IdDict([itr])
```

`IdDict{K,V}()` は、ハッシュとして [`objectid`](@ref) を使用し、等価性として `===` を使用して、型 `K` のキーと型 `V` の値を持つハッシュテーブルを構築します。

さらなるヘルプについては [`Dict`](@ref) を参照してください。以下の例では、`Dict` のキーはすべて `isequal` であり、そのため同じようにハッシュ化され、上書きされます。`IdDict` はオブジェクトIDでハッシュ化されるため、3つの異なるキーを保持します。

# 例

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} with 1 entry:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} with 3 entries:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
