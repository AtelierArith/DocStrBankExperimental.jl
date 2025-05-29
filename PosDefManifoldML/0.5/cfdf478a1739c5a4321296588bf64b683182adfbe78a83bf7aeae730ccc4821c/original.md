```julia
macro pipeline(args...)
```

Create a [`Pipeline`](@ref) chaining the provided expressions.

As an example, the sintax is:

```julia
p = @pipeline Recenter() → Compress → Shrink(Fisher; threaded=false)
```

Note that:

  * The symbol → (escape "\to") separating the conditioners is optional.
  * This macro has alias `@→`.
  * As in the example above, expressions may be instantiated conditioners, like `Recenter()`, or their type, like `Compress`, in which case the default conditioner of that type is created.

The example above is thus equivalent to

```julia
    p = @→ Recenter() Compress() Shrink(Fisher; threaded=false)
```

Conditioners are not callable by the macro. Thus if you want to pass a variable, do not write

```julia
    R = Recenter()
    p = @→ R
```

but 

```julia
    R = Recenter()
    p = @→ eval(R)
```

**Available conditioners to form pipelines**

[`Tikhonov`](@ref), [`Recenter`](@ref), [`Compress`](@ref), [`Equalize`](@ref), [`Shrink`](@ref)

**See also**: [`fit!`](@ref), [`transform!`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

P=randP(3, 5)
pipeline = fit!(P, @→ Recenter → Compress)
```
