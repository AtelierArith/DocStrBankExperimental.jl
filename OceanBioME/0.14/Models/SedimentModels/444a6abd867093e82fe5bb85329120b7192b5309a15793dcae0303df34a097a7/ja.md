```
単層「マルチG」堆積物モデル（`SimpleMultiG`）を`grid`上に作成し、パラメータをオプションで指定できます。

このモデルは単層（すなわち、孔性拡散を含まない）モデルで、異なる速度（速い、遅い、耐久性）で分解する3つのクラスの堆積有機物を持っています。硝化/脱窒/無酸素鉱化の割合は、Soetaert et al. 2000のパラメータ化にデフォルト設定されています; doi:[10.1016/S0012-8252(00)00004-0](https://doi.org/10.1016/S0012-8252(00)00004-0)。

このモデルはまだ検証されておらず、観測データと比較されていません。分解プロセスの多様性は酸素の可用性に強く依存する可能性があるため（[https://bg.copernicus.org/articles/6/1273/2009/bg-6-1273-2009.pdf](https://bg.copernicus.org/articles/6/1273/2009/bg-6-1273-2009.pdf)を参照）、酸素モデルも徹底的に検証することが重要です（現在も制限されています）。

# 例

```

jldoctest simplemultig; filter = r".*@ OceanBioME.Models.Sediments.*" julia> using OceanBioME, Oceananigans

julia> grid = RectilinearGrid(size=(3, 3, 30), extent=(10, 10, 200));

julia> sediment_model = SimpleMultiGSediment(grid) `BiogeochemicalSediment` with `Single-layer multi-G sediment model (Float64)` biogeochemistry     Prognostic fields: (:Ns, :Nf, :Nr)     Tracked fields: (:NO₃, :NH₄, :O₂, :sPOM, :bPOM)     Coupled fields: (:NO₃, :NH₄, :O₂)

julia> biogeochemistry = LOBSTER(; grid, sediment_model) LOBSTER{Float64} with carbonates ❌, oxygen ❌, variable Redfield ratio ❌ and (:sPOM, :bPOM) sinking  Light attenuation: Two-band light attenuation model (Float64)  Sediment: `BiogeochemicalSediment` with `Single-layer multi-G sediment model (Float64)` biogeochemistry  Particles: Nothing  Modifiers: Nothing

```
