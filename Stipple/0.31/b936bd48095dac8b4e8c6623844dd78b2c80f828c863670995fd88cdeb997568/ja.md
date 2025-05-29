```
    mutable struct Reactive{T} <: Observables.AbstractObservable{T}
```

`Reactive` はモデルによって扱われる変数の基本型です。これは `AbstractObservable` であり、その内容は `Reactive` 変数の名前の後に `[]` を付けることで取得されます。便利のために、`Reactive` は `R` で省略することができます。

Reactive 変数を作成する方法はいくつかあります：

  * `r = Reactive(8)`
  * `r = Reactive{Float64}(8)`
  * `r = Reactive{Float64}(8, READONLY)`
  * `r = Reactive{String}("Hello", PRIVATE)`
  * `r = Reactive(jsfunction"console.log('Hi')", JSFUNCTION)`
