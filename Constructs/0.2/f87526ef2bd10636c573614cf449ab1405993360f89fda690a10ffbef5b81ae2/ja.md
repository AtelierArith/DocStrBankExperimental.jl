```
SizedArray([TA], T|element, size...) -> Construct{TA}
```

特定のサイズと要素を持つ配列を構築します。

# 引数

  * `TA<:AbstractArray{T}`: 対象の配列タイプ、デフォルトは `Array{T, N}` です。
  * `T`: 要素の型。
  * `element::Construct{T}`: 要素の構成。
  * `size`: 配列のサイズ。
