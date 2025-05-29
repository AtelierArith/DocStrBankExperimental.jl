```
cosmology(; h = 0.69,
            Neff = 3.04,
            OmegaK = 0,
            OmegaM = 0.29,
            OmegaR = nothing,
            Tcmb = 2.7255,
            w0 = -1,
            wa = 0)
```

# パラメータ

  * `h` - 無次元ハッブル定数
  * `Neff` - 質量のないニュートリノ種の有効数; Ω_νを計算するために使用
  * `OmegaK` - 曲率密度 (Ω_k)
  * `OmegaM` - 物質密度 (Ω_m)
  * `OmegaR` - 放射密度 (Ω_r)
  * `Tcmb` - ケルビンでのCMB温度; Ω_γを計算するために使用
  * `w0` - CPLダークエネルギー状態方程式; `w = w0 + wa(1-a)`
  * `wa` - CPLダークエネルギー状態方程式; `w = w0 + wa(1-a)`

# 例

```jldoctest
julia> c = cosmology()
Cosmology.FlatLCDM{Float64}(0.69, 0.7099122024007928, 0.29, 8.77975992071536e-5)

julia> c = cosmology(OmegaK=0.1)
Cosmology.OpenLCDM{Float64}(0.69, 0.1, 0.6099122024007929, 0.29, 8.77975992071536e-5)

julia> c = cosmology(w0=-0.9, OmegaK=-0.1)
Cosmology.ClosedWCDM{Float64}(0.69, -0.1, 0.8099122024007929, 0.29, 8.77975992071536e-5, -0.9, 0.0)
```
