```
shrink(x)
```

入力を縮小します。返される値は、`x`に「類似した」要素を持つ`Vector`です。長さ1のベクターを返すことは、これ以上の縮小が不可能であることを意味します。

# デフォルトのシュリンカー

このパッケージには、以下の型に対する`shrink`メソッドが含まれています：

  * `AbstractString`
  * `AbstractArray{T, N}` すべての `T` と `N` に対して

# 実装

  * `shrink(x::T)`の任意の実装は、[`shrinkable(x::T)`](@ref shrinkable(Any))の実装を伴わなければなりません。これを怠ると、[`@quickcheck`](@ref)が型`T`のオブジェクトに対して`shrink`を呼び出すことができなくなります。
  * `shrink(x)`は、`shrinkable(x)`が`false`に評価される場合、[x]を返さなければなりません。メソッドの最初の行は次のようにすることをお勧めします：

```julia
shrinkable(x) || return typeof(x)[x]
```
