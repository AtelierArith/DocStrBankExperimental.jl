```
op_string(mime::MIME, x::GenericNonlinearExpr, ::Val{op}) where {op}
```

`mime`と`x`を使って[`function_string`](@ref)が呼び出されたときに印刷されるべき演算子`op`の文字列を返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2], Bin);

julia> f = @expression(model, x[1] || x[2]);

julia> op_string(MIME("text/plain"), f, Val(:||))
"||"
```
