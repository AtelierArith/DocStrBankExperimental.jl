```
BareInterval{T<:NumTypes}
```

IEEE標準1788-2015に従った区間演算による計算を保証するための区間型です。[`Interval`](@ref)とは異なり、このベア区間には装飾がなく、`Real`のサブタイプではなく、`BareInterval`と`Number`を混合した演算ではエラーが発生します。

フィールド:

  * `lo :: T`
  * `hi :: T`

IEEE標準1788-2015に準拠したコンストラクタ: [`bareinterval`](@ref)。

参照: [`Interval`](@ref)。
