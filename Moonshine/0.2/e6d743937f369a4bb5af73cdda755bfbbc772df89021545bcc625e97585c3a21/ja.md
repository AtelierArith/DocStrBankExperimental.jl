```julia
abstract type Distance{T}
```

2つの [`Sequence`](@ref) の間の距離。

# 実装

距離 `D<:Distance` が木の構築に使用可能であるために必要な唯一のメソッドは

```
distance(::D{T}, ::Sequence, ::Sequence) where T
```

デフォルトコンストラクタを実装することも便利です。例えば、`D` が離散距離である場合、

```
D() = D{Int}()
```
