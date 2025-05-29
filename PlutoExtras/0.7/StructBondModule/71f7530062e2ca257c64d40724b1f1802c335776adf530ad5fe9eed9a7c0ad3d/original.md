```
@fieldbond typename block
```

Convenience macro to define custom widgets for each field of `typename`. This is mostly inteded to be used in combintation with [`StructBond`](@ref).

Given for example the following structure

```
Base.@kwdef struct ASD
	a::Int 
	b::Int
	c::String
end
```

one can create a nice widget to create instances of type `ASD` wih the following code:

```
@fieldbond ASD begin
	a = Slider(1:10)
	b = Scrubbable(1:10)
	c = TextField()
end
@fielddescription ASD begin
	a = md"Magical field with markdown description"
	b = @htl "<span>Field with HTML description</span>"
	c = "Normal String Description"
end
@bind asd StructBond(ASD)
```

where `asd` will be an instance of type `ASD` with each field interactively controllable by the specified widgets and showing the field description next to each widget.

See also: [`BondTable`](@ref), [`StructBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
