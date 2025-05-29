```
Stacked(bs)
Stacked(bs, ranges)
stack(bs::Bijector...)
```

複数のビジェクタを一緒にスタックする `Bijector` で、`bs[i]::Bijector` が `x[ranges[i]]::UnitRange{Int}` に適用されるベクトルに適用できます。

# 引数

  * `bs` は 0 次元および/または 1 次元のビジェクタの `Tuple` または `AbstractArray` である必要があります。

      * `bs` が `Tuple` の場合、実装は生成関数を使用して型安定です。
      * `bs` が `AbstractArray` の場合、実装は型安定ではなく、反復的な方法を使用します。
  * `ranges` は `UnitRange{Int}` からなる反復可能なものである必要があります。

      * `length(bs) == length(ranges)` が真である必要があります。

# 例

```
b1 = Logit(0.0, 1.0)
b2 = identity
b = stack(b1, b2)
b([0.0, 1.0]) == [b1(0.0), 1.0]  # => true
```
