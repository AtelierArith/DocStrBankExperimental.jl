```
@NTBond description block
@NTBond description block transform_function
```

Convenience macro to create a [`StructBond`](@ref) wrapping a NamedTuple with field names provided in the second argument `block`.

Useful when one wants a quick way of generating a bond that creates a NamedTuple. An example usage is given in the code below:

```
@bind nt @NTBond "My Fancy NTuple" begin
	a = ("Description", Slider(1:10))
	b = (md"*Bold* field", Slider(1:10))
	c = Slider(1:10) # No description, defaults to the name of the field
end
```

which will create a `NamedTuple{(:a, :b, :c)}` and assign it to variable `nt`.

When calling the macro with a third argument, this is interpreted as a function that is used to create a bond transformation using `PlutoUI.Experimental.transformed_value`.

This means that the two expressions below yield the same result:

```julia
@NTBond "WoW" begin
	a = ("Description", Slider(1:10))
end x -> x.a + 2
```

and

```julia
PlutoUI.Experimental.transformed_value(x -> x.a + 2, @NTBond "WoW" begin
	a = ("Description", Slider(1:10))
end)
```

See also: [`BondTable`](@ref), [`@NTBond`](@ref), [`@BondsList`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddata`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
