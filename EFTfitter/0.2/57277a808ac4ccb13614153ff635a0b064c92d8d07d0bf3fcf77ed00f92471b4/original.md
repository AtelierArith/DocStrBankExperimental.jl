```
struct Observable
```

Fields:  

  * `prediction::Function`: Function returning the predicted value of the observable as a function of the parameters.
  * `min::Real`: Minimum boundary for values of the observable. Defaults to `-Inf`.
  * `max::Real`: Maximum boundary for values of the observable. Defaults to `Inf`.
  * `weight::Real`: Weight of this observable in the combination. Defaults to `1.0`.

Constructors:

```julia
Observable(
    prediction::Function
    min::Real = -Inf
    max::Real = Inf
    weight::Real = 1.0
)
```
