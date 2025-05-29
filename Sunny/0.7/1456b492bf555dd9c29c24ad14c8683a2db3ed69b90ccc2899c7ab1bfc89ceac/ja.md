```
global_position(sys::System, site::Site)
```

[`Site`](@ref) のグローバル座標における位置。

フルリストの位置を事前に計算するには、以下のように [`eachsite`](@ref) を使用できます。

```julia
pos = [global_position(sys, site) for site in eachsite(sys)]
```
