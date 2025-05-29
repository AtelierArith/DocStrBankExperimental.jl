```
NormalOp(T::Type; parent, weights)
```

`parent`の遅延正規演算子で、オプションの重み演算子`weights`を持ちます。`adjoint(parent) * weights * parent`を計算します。

# 必須引数

  * `T`                        - 要素の型、例えば`ComplexF32`の場合は`Float64`

# 必須キーワード引数

  * `parent`                   - 基本演算子

# オプションキーワード引数

  * `weights`                  - 正規演算子のためのオプションの重み。すでに`weights = adjoint.(w) .* w`の形である必要があります。
