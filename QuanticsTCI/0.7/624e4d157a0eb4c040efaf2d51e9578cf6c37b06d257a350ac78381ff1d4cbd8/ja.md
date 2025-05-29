```
function quanticscrossinterpolate(
    ::Type{ValueType},
    f,
    xvals::AbstractVector{<:AbstractVector},
    initialpivots::Union{Nothing,AbstractVector{<:AbstractVector}}=nothing;
    unfoldingscheme::Symbol=:interleaved,
    nrandominitpivot=5,
    kwargs...
) where {ValueType}
```

関数 $f(\mathbf{x})$ を量子テンソル列として補間します。このオーバーロードは、`xvals` に与えられた $\mathbf{x}$ 点から自動的に Grid オブジェクトを構築します。

引数:

  * `xvals::AbstractVector{<:AbstractVector}`: `f` を評価できる離散点のセットで、配列のセットとして与えられ、`xvals[i]` は `i` 番目の軸を説明します。`xvals` の各配列は、ある整数 `R` に対して `2^R` 点を含む必要があります。
  * その他の引数については、メインオーバーロードのドキュメントを参照してください。
