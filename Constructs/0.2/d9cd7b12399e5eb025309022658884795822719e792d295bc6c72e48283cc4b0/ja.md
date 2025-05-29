```
Adapter(T|subcon, encode) -> SymmetricAdapter{T}
SymmetricAdapter(T|subcon, encode) -> SymmetricAdapter{T}
```

`encode` 関数に基づいて対称アダプタを作成します。

# 引数

  * `subcon::Construct{T}`: 基本となる構造体。
  * `encode`: エンコーディング関数。この関数は `(::T; contextkw...)->T` のようなシグネチャを持ち、自己反転性 (`encode(encode(x)) == x`) を満たす必要があります。
