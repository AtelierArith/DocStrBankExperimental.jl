```
analytic_synchrotron_HB07( rho_cgs::Array{<:Real}, m_cgs::Array{<:Real}, hsml_cgs::Array{<:Real},
                           B_cgs::Array{<:Real}, T_keV::Array{<:Real}, Mach::Array{<:Real},
                           θ_B::Union{Nothing, Array{<:Real}}=nothing;
                           xH::Real=0.752, ν0::Real=1.4e9, z::Real=0.0,
                           dsa_model::Union{Nothing,Integer,AbstractShockAccelerationEfficiency}=nothing,
                           ξe::Real=1.e-5,
                           show_progress::Bool=false )
```

[Hoeft&Brüggen (2007)](https://ui.adsabs.harvard.edu/abs/2007MNRAS.375...77H/abstract)で説明されている簡略化されたアプローチに従って、[Wittor et. al. (2017)](https://ui.adsabs.harvard.edu/abs/2017MNRAS.464.4448W/abstract)によるアプローチに従って、解析的シンクロトロン放射を計算します。

シンクロトロン放射率 `j_nu` を単位 [erg/s/Hz/cm^3] で返します。

## 引数

  * `rho_cgs::Array{<:Real}`:  密度 $g/cm^3$ で。
  * `m_cgs::Array{<:Real}`:    粒子の質量 $g$ で。
  * `hsml_cgs::Array{<:Real}`: `HSML` ブロック $cm$ で。
  * `B_cgs::Array{<:Real}`:    磁場 $G$ で。
  * `T_keV::Array{<:Real}`:    温度 $keV$ で。
  * `Mach::Array{<:Real}`:     音速マッハ数。
  * `θ_B::Union{Nothing,Array{<:Real}}=nothing`: 衝撃の傾斜（オプション）。

## キーワード引数

  * `xH::Float64 = 0.76`:        化学モデルなしで実行する場合のシミュレーションの水素比。
  * `ν0::Real=1.44e9`:           観測周波数 $Hz$ で。
  * `z::Real=0.0`:               シミュレーションの赤方偏移。
  * `dsa_model=nothing`:         拡散衝撃加速モデル。値を設定すると、デフォルトのHoeft&Brüggen加速モデルが上書きされます。次のセクションを参照してください。
  * `ξe::Real=1.e-5`:            CR陽子と電子エネルギー加速の比率。熱ガスの割合として与えられ、実質的には `Xcr * Kep` です。Nuza+2017からのデフォルト値。`dsa_model != nothing` の場合は、`ξe = 1.e-4` のような値を使用してください。
  * `show_progress::Bool=false`: true に設定するとプログレスバーが有効になります。

## DSAモデル

自己定義の `AbstractShockAccelerationEfficiency`（詳細は [DiffusiveShockAccelerationModels.jl](https://github.com/LudwigBoess/DiffusiveShockAccelerationModels.jl) を参照！）または数値値を入力として受け取ります。数値値は次のように対応します：

  * `0`: [Kang et. al. (2007)](https://ui.adsabs.harvard.edu/abs/2007ApJ...669..729K/abstract)
  * `1`: [Kang & Ryu (2013)](https://ui.adsabs.harvard.edu/abs/2013ApJ...764...95K/abstract)
  * `2`: [Ryu et. al. (2019)](https://ui.adsabs.harvard.edu/abs/2019ApJ...883...60R/abstract)
  * `3`: [Caprioli & Spitkovsky (2014)](https://ui.adsabs.harvard.edu/abs/2014ApJ...783...91C/abstract)
  * `4`: [Pfrommer et. al. (2006)](https://ui.adsabs.harvard.edu/abs/2006MNRAS.367..113P/abstract)

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`

```
