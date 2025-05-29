```
get_cosmology(::Type{T}; h=0.69, Neff=3.04, OmegaK=0.0,
    OmegaM=0.29, OmegaR=nothing, Tcmb=2.7255, w0=-1, wa=0)
```

背景宇宙論を構築します。この関数は、指定された数値型での計算を行うために、Cosmology.jlのcosmology()関数を複製します。

# 引数:

  * `::Type{T}`: 計算に使用する数値型

# キーワード

  * `h` - 無次元ハッブル定数
  * `OmegaK` - 曲率密度 (Ω_k)
  * `OmegaM` - 物質密度 (Ω_m)
  * `OmegaR` - 放射密度 (Ω_r)
  * `Tcmb` - ケルビンでのCMB温度; Ω_γを計算するために使用
  * `Neff` - 質量のないニュートリノ種の有効数; Ω_νを計算するために使用
  * `w0` - CPLダークエネルギー状態方程式; `w = w0 + wa(1-a)`
  * `wa` - CPLダークエネルギー状態方程式; `w = w0 + wa(1-a)`

# 例

```julia-repl
julia> get_cosmology(Float32; h=0.7)
Cosmology.FlatLCDM{Float32}(0.7f0, 0.7099147f0, 0.29f0, 8.5307016f-5)
```
