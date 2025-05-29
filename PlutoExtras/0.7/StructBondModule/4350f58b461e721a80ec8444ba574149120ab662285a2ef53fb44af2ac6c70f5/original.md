```
@popoutasfield T
@popoutasfield T1 T2 ...
```

This macro will make the default widget for fields of type `T` a [`Popout`](@ref) wrapping a `StructBond{T}` type. For this to work, the `StructBond{T}` must have a default widget associated to each of its field, either by using [`@fieldbond`](@ref) or [`@typeasfield`](@ref)

# Example (in Pluto)

```julia
# ╔═╡ 8db82e94-5c81-4c52-9228-7e22395fb68f
using PlutoExtras.StructBondModule

# ╔═╡ 86a80228-f495-43e8-b1d4-c93b7b52c8d8
begin
	@kwdef struct MAH
		a::Int
	end
	@kwdef struct BOH
		mah::MAH
	end
	
	# This will make the default widget for an Int a Slider
	@typeasfield Int = Slider(1:10)
	# This will make the default widget for fields of type ASD a popout that wraps a StructBond{ASD}
	@popoutasfield MAH
	
	@bind boh StructBond(BOH)
end

# ╔═╡ 2358f686-1950-40f9-9d5c-dac2d98f4c24
boh === BOH(MAH(1))
```
