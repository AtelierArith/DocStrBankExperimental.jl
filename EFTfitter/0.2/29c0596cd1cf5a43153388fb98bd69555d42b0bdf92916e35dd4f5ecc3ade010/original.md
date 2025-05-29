```
struct Measurement
```

Fields:  

  * `observable::Observable`: Observable that is measured.
  * `value::Real;`: Measured value.
  * `uncertainties::NamedTuple{<:Any, <:Tuple{Vararg{Real}}}`: Uncertainties of the measurement as NamedTuple.
  * `active::Bool`: Use or exclude measurement in fit. Defaults to `true`.

Constructors:

```julia
Measurement(
    observable::Observable,
    value::Real;
    uncertainties::NamedTuple{<:Any, <:Tuple{Vararg{Real}}},
    active::Bool = true
)
```

```julia
Measurement(
    observable::Function,
    value::Real;
    uncertainties::NamedTuple{<:Any, <:Tuple{Vararg{Real}}},
    active::Bool = true
)
```
