```
gamma_c_target(surface, ζ_range, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surf, ζMin, ζStep, ζMax, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surf, ζMin, ζStep, ζMax, BResolution, comm, epsEff = true, gammaC = true)
```

# 引数

  * `surf::Surface`: VMECまたはDESCの表面（コードは平衡と表面のリスト、または単一の表面のいずれかを必要とします）
  * `ζ_range <: AbstractRange`: ラジアンでのトロイダル角度の値の範囲
  * `BResolution::Int`: Bフィールドの積分の解像度
  * `comm::MPI:Comm`: 含まれている場合、コードはMPIインターフェースを使用して計算を高速化します
  * `epsEff::Bool=true`: オプションの引数、デフォルトはtrue。trueの場合、コードは$\epsilon_\mathrm{eff}$の値を計算して返します
  * `gammac::Bool=true`: オプションの引数、デフォルトはtrue。trueの場合、コードは$\Gamma_c$の値を計算して返します

# 出力:

  * オプションのブール引数に応じて$\epsilon_\mathrm{eff}$および/または$\Gamma_c$を計算する値のタプル。両方が存在する場合（デフォルト）、それらは$(\epsilon_\mathrm{eff}, \Gamma_c)$のペアの形で返されます。
