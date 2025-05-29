```
and_then(f, ::Type{T}, x::Result{O, E})::Result{T, E}
```

もし `x` が結果値であれば、`Result{T, E}(Ok(f(unwrap(x))))` を返し、そうでなければエラー値を返します。常に `Result{T, E}` を返します。

**警告** `f(unwrap(x))` が `T` でない場合、この関数はエラーをスローします。

# 例

```jldoctest
julia> and_then(join, String, some(["ab", "cd"]))
some("abcd")

julia> and_then(i -> Int32(ncodeunits(join(i))), Int32, none(Vector{String}))
none(Int32)
```
