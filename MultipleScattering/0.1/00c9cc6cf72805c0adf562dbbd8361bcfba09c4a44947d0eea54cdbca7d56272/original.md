```
RegularSource(medium::P, field::Function, coef::Function)
```

Is a struct type which describes the source field that drives/forces the whole system. It is also known as an incident wave. It has three fields `RegularSource.medium`, `RegularSource.field`, and `RegularSource.coef`.

The source field at the position 'x' and angular frequency 'ω' is given by

```julia-repl
x = [1.0,0.0]
ω = 1.0
RegularSource.field(x,ω)
```

The field `RegularSource.coef` regular*basis*function(medium::Acoustic{T,2}, ω::T)
