```
popoutwrap(T)
```

Convenience function to construct a `Popout` wrapping a `StructBond` of type `T`. This is convenient when one wants to create nested `StructBond` types.

Given for example the following two structures

```
Base.@kwdef struct ASD
	a::Int 
	b::Int
	c::String
end
Base.@kwdef struct LOL
	asd::ASD 
	text::String
end
```

one can create a nice widget to create instances of type `LOL` that also include a popout of widget generating `ASD` wih the following code:

```
# Define the widget for ASD
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

# Define the widget for LOL
@fieldbond LOL begin
	asd = popoutwrap(ASD)
	text = TextField(;default = "Some Text")
end
@fielddescription LOL begin
	asd = "Click on the icon to show the widget to generate this field"
	text = "Boring Description"
end
@bind lol StructBond(LOL)
```

where `lol` will be an instance of type `LOL` with each field interactively controllable by the specified widgets and showing the field description next to each widget.

See also: [`BondTable`](@ref), [`StructBond`](@ref), [`Popout`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
