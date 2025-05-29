```
@enumbatteries T [options]
```

Automatically derive several methods for Enum type `T`.

# Example

```julia
@enum Color Red Blue Yellow
@enumbatteries Color
@enumbatteries Color hash=false # don't overload `Base.hash`
@enumbatteries Color symbol_conversion=true # allow convert(Color, :Blue), Color(:Blue), convert(Symbol, Blue), Symbol(Blue)
```

Supported options and defaults are:

  * **string_conversion** = false:

Add `convert(MyEnum, ::String)`, `MyEnum(::String)`, `convert(String, ::MyEnum)` and `String(::MyEnum)`

  * **symbol_conversion** = false:

Add `convert(MyEnum, ::Symbol)`, `MyEnum(::Symbol)`, `convert(Symbol, ::MyEnum)` and `Symbol(::MyEnum)`

  * **selfconstructor** = true:

Add a constructor of the for `T(self::T) = self`

  * **hash** = false:

Define `Base.hash` structurally.

  * **typesalt** = nothing:

Only used if `hash=true`. In this case the `hash` will be purely computed from `typesalt` and `hash_eq_as(obj)`. The type `T` will not be used otherwise. This makes the hash more likely to stay constant, when executing on a different machine or julia version
