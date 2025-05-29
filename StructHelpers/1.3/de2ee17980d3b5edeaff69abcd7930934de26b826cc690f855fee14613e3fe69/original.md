```
@batteries T [options]
```

Automatically derive several methods for type `T`.

# Example

```julia
struct S
    a
    b
end

@batteries S
@batteries S hash=false # don't overload `Base.hash`
@batteries S kwconstructor=true # add a keyword constructor
```

Supported options and defaults are:

  * **eq** = true:

Define `Base.(==)` structurally.

  * **isequal** = true:

Define `Base.isequal` structurally.

  * **hash** = true:

Define `Base.hash` structurally.

  * **kwconstructor** = false:

Add a keyword constructor.

  * **selfconstructor** = true:

Add a constructor of the for `T(self::T) = self`

  * **kwshow** = false:

Overload `Base.show` such that the names of each field are printed.

  * **getproperties** = true:

Overload `ConstructionBase.getproperties`.

  * **constructorof** = true:

Overload `ConstructionBase.constructorof`.

  * **typesalt** = nothing:

Only used if `hash=true`. In this case the `hash` will be purely computed from `typesalt` and `hash_eq_as(obj)`. The type `T` will not be used otherwise. This makes the hash more likely to stay constant, when executing on a different machine or julia version

  * **StructTypes** = false:

Overload `StructTypes.StructType` to be `Struct()`. Needs the `StructTypes.jl` package to be installed.

See also [`hash_eq_as`](@ref)
