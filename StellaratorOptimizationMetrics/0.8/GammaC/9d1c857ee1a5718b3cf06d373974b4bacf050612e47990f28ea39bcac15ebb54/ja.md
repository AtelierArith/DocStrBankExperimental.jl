```
gamma_c_target(surfaces, eq, ζ_range, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surfaces, eq, ζMin, ζStep, ζMax, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surfaces, eq, ζMin, ζStep, ζMax, BResolution, comm, epsEff = true, gammaC = true)
```

$$
\Gamma_c
$$

を1つまたは複数の表面から計算する関数（MPIの有無にかかわらず）

# 引数

  * `surfaces::Union{T, Vector{T}}`: $\Gamma_c$を計算する表面を与える単一の浮動小数点数または浮動小数点数のベクトル。これらの値は正規化トロイダルフラックス$s$で与えられます。
  * `eq::E`: VmecまたはDESCの平衡
  * `BResolution::Int`: B場の積分の解像度
  * `comm::MPI:Comm`: 含まれている場合、コードはMPIインターフェースを使用して計算を高速化します。
  * `epsEff::Bool=true`: デフォルトはtrueのオプション引数。trueの場合、コードは$\epsilon_\mathrm{eff}$の値を計算して返します。
  * `gammac::Bool=true`: デフォルトはtrueのオプション引数。trueの場合、コードは$\Gamma_c$の値を計算して返します。

# 出力:

  * `targetValues::Vector{T}`: オプションのブール引数に応じて$\epsilon_\mathrm{eff}$および/または$\Gamma_c$を計算する値の配列。両方が存在する場合（デフォルト）、それらは$(\epsilon_\mathrm{eff}, \Gamma_c)$のペアの形式で返されます。
