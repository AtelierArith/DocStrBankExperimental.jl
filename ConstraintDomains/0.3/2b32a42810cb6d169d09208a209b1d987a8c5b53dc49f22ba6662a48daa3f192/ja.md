```
AbstractDomain
```

任意のドメインタイプのための抽象スーパタイプ。ドメインタイプ `D <: AbstractDomain` は、`AbstractDomain` と適切にインターフェースするために以下のメソッドを実装する必要があります。

  * `Base.∈(val, ::D)`
  * `Base.rand(::D)`
  * `Base.length(::D)` これは離散ドメインの要素数、または連続ドメインの境界間の距離などです。

さらに、ドメインが動的コンテキストで使用される場合、次のメソッドを拡張できます。

  * `add!(::D, args)`
  * `delete!(::D, args)`

ここで `args` は `D` の構造に依存します。
