```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    size::NTuple{d,Int},
    initialpivots::AbstractVector{<:AbstractVector}=[ones(Int, d)];
    unfoldingscheme::Symbol=:interleaved,
    kwargs...
) where {ValueType,d}
```

テンソル $F$ を量子テンソル列として補間します。引数などの説明については、メインオーバーロードのドキュメントを参照してください。
