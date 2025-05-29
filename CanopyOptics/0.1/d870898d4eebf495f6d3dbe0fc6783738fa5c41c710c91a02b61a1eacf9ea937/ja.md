```
prospect(leaf::LeafProspectProProperties{FT},
                optis) where {FT<:AbstractFloat}
```

PROSPECT-PROに基づいて葉の光学特性（反射率と透過率）を計算します。

# 引数

  * `leaf`  [`LeafProspectProProperties`](@ref) 型の構造体で、葉の組成を提供します。
  * `optis` [`LeafOpticalProperties`](@ref) 型の構造体で、吸収断面積とスペクトルグリッドを提供します。

# 例

```julia-repl
julia> opti = createLeafOpticalStruct((400.0:5:2400)*u"nm");
julia> leaf = LeafProspectProProperties{Float64}(Ccab=30.0);
julia> T,R = prospect(leaf,opti);
```
