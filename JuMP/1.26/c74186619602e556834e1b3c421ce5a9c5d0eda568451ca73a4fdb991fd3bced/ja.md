```
coefficient(v1::GenericVariableRef{T}, v2::GenericVariableRef{T}) where {T}
```

`v1` と `v2` が等しい場合は `one(T)` を返し、それ以外の場合は `zero(T)` を返します。

これは、式が単一の変数である場合のコードを簡素化するための他の [`coefficient`](@ref) メソッドのフォールバックです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> coefficient(x[1], x[1])
1.0

julia> coefficient(x[1], x[2])
0.0
```
