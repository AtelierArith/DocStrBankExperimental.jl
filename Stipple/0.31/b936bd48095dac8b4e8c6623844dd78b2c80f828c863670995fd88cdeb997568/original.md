```
    mutable struct Reactive{T} <: Observables.AbstractObservable{T}
```

`Reactive` is a the base type for variables that are handled by a model. It is an `AbstractObservable` of which the content is obtained by appending `[]` after the `Reactive` variable's name. For convenience, `Reactive` can be abbreviated by `R`.

There are several methods of creating a Reactive variable:

  * `r = Reactive(8)`
  * `r = Reactive{Float64}(8)`
  * `r = Reactive{Float64}(8, READONLY)`
  * `r = Reactive{String}("Hello", PRIVATE)`
  * `r = Reactive(jsfunction"console.log('Hi')", JSFUNCTION)`
