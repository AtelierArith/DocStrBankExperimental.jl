```
struct GenAvailability <: Availability
```

参照 `Availability` ノード。参照 `Availability` ノードは、すべての接続されたフローのエネルギーバランスを解決します。

# フィールド

  * **`id`** はノードの名前/識別子です。
  * **`inputs::Vector{<:Resource}`** は入力 [`Resource`](@ref)s です。
  * **`output::Vector{<:Resource}`** は出力 [`Resource`](@ref)s です。

コンストラクタが提供されており、フィールドには単一の配列のみを提供できます：

  * **`id`** はノードの名前/識別子です。
  * **`𝒫::Vector{<:Resource}`** は `[`Resource`](@ref)s です。
