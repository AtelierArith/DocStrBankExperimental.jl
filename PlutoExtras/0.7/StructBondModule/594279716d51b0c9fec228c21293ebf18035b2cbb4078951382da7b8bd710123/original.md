```
@fielddata typename block
```

Convenience macro to define custom widgets for each field of `typename`. This is mostly inteded to be used in combintation with [`StructBond`](@ref).

Given for example the following structure `ASD`, one can create a nice widget to create instances of type `ASD` wih the following code:

```
begin
Base.@kwdef struct ASD
	a::Int 
	b::Int
	c::String
	d::String
end
@fielddata ASD begin
	a = (md"Magical field with markdown description", Slider(1:10))
	b = (@htl("<span>Field with HTML description</span>"), Scrubbable(1:10))
	c = ("Normal String Description", TextField())
	d = TextField()
end
@bind asd StructBond(ASD)
end
```

where `asd` will be an instance of type `ASD` with each field interactively controllable by the specified widgets and showing the field description next to each widget. The rightside argument of each `:(=)` in the `block` can either be a single element or a tuple of 2 elements. In case a single elemnent is provided, the provided value is interpreted as the `fieldbond`, so the bond/widget to show for that field.  If two elements are given, the first is assigned to the description and the second as the bond to show

See also: [`BondTable`](@ref), [`StructBond`](@ref), [`@NTBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
