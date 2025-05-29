```
@typeasfield T = Widget
@typeasfield begin
	T1 = Widget1
	T2 = Widget2
	...
end
```

Macro to give a default widget for a specific type `T`, `T1`, or `T2`. This can be over-ridden by specifying a more specific default for a custom type using [`@fieldbond`](@ref) When a custom type is wrapped inside a [`StructBond`](@ref) and a custom widget for one of its field is not defined, the show method will use the one defined by this macro for the field type.

# Examples

The following julia code will error because a default widget is not defined for field `a`

```
using PlutoExtras.StructBondModule
struct ASD 
	a::Int
end
StructBond(ASD)
```

Apart from defining a specific value for `ASD` with [`@fieldbond`](@ref), one can also define a default widget for Int with:

```julia
@typeasfield Int = Slider(1:10)
```

Now calling `StructBond(ASD)` will not error and will default to showing a `Slider(1:10)` as bond for field `a` of `ASD`.
