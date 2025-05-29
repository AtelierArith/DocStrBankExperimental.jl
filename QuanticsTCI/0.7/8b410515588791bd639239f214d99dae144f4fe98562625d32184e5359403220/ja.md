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

関数 $f(\mathbf{x})$ を量子テンソル列として補間します。このオーバーロードは、`size` に含まれる情報を使用して自動的に Grid オブジェクトを構築します。ここで、$i$ 番目の引数は $1$ から $size[i]$ までの範囲で実行されます。
