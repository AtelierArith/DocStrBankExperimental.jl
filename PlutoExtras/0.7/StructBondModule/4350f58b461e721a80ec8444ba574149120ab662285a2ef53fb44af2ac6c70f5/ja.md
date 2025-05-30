```
@popoutasfield T
@popoutasfield T1 T2 ...
```

このマクロは、型 `T` のフィールドのデフォルトウィジェットを `StructBond{T}` 型をラップした [`Popout`](@ref) にします。これが機能するためには、`StructBond{T}` の各フィールドに関連付けられたデフォルトウィジェットが必要であり、それは [`@fieldbond`](@ref) または [`@typeasfield`](@ref) を使用することで実現できます。

# 例 (Pluto)

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
	
	# これにより、Int のデフォルトウィジェットがスライダーになります
	@typeasfield Int = Slider(1:10)
	# これにより、型 ASD のフィールドのデフォルトウィジェットが StructBond{ASD} をラップしたポップアウトになります
	@popoutasfield MAH
	
	@bind boh StructBond(BOH)
end

# ╔═╡ 2358f686-1950-40f9-9d5c-dac2d98f4c24
boh === BOH(MAH(1))
```
