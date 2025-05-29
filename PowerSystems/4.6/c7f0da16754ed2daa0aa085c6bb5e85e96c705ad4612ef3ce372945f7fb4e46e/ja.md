```julia
get_subcomponents(
    hybrid::PowerSystems.HybridSystem
) -> Channel{Any}

```

ハイブリッドシステム内のサブコンポーネントに対するイテレータを返します。

# 例

```julia
for subcomponent in get_subcomponents(hybrid_sys)
    @show subcomponent
end
subcomponents = collect(get_subcomponents(hybrid_sys))
```
