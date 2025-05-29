```
flatmap(function_returning_A, a::A)::A
```

`flatmap` は関数をコンテナに適用し、すぐにフラットにします。map が `A{A{...}}` を返すのに対し、flatmap はネストなしのプレーンな `A{...}` を返します。

独自の flatmap バージョンを定義する場合、`f` を適用した後に `Base.convert` を適用することをお勧めします。これにより、flatmap が型安全であり、他の型との健全な相互作用を可能にします。これらの型はあなたの A に変換可能であるかもしれません。

例えば、Vector の実装は次のようになります：

```
TypeClasses.flatmap(f, v::Vector) = vcat((convert(Vector, f(x)) for x in v)...)
```
