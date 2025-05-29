```
ScalarShape{T} <: AbstractScalarShape{T}
```

An `ScalarShape` describes the shape of scalar values of a given type.

Constructor:

```
ScalarShape{T::Type}()
```

T may be an abstract type of Union, or a specific type, e.g.

```
ScalarShape{Real}()
ScalarShape{Integer}()
ScalarShape{Float32}()
ScalarShape{Complex}()
```

Scalar shapes may have a total number of degrees of freedom (see [`totalndof`](@ref)) greater than one, e.g. shapes of complex-valued scalars:

```
totalndof(ScalarShape{Real}()) == 1
totalndof(ScalarShape{Complex}()) == 2
```

See also the documentation of [`AbstractValueShape`](@ref).
