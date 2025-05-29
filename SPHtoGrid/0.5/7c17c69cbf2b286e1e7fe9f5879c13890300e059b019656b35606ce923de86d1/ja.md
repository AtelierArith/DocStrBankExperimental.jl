```
analytic_synchrotron_GS( rho_cgs::Array{<:Real}, B_cgs::Array{<:Real},
                         T_K::Array{<:Real}, Mach::Array{<:Real};
                         xH::Real=0.76, dsa_model::Integer=1, ν0::Real=1.44e9,
                         integrate_pitch_angle::Bool=true )
```

Ginzburg & Syrovatskii 1965の「Cosmic Magnetobremsstrahlung」で説明されている簡略化されたアプローチを用いて、解析的なシンクロトロン放射を計算します。[Donnert et. al. (2016)](https://ui.adsabs.harvard.edu/abs/2016MNRAS.462.2014D/abstract)の実装を使用しています。

シンクロトロン放射強度 `j_nu` を単位 [erg/s/Hzcm^3] で返します。

# 引数

  * `rho_cgs::Array{<:Real}`: 密度 $g/cm^3$ で。
  * `B_cgs::Array{<:Real}`:   ガウス単位の磁場。
  * `T_K::Array{<:Real}`:     ケルビン単位の温度。
  * `Mach::Array{<:Real}`:    マッハ数。
  * `θ_B::Union{Nothing,Array{<:Real}}=nothing`: 衝撃の傾斜（オプション）。

## キーワード引数

  * `xH::Float64 = 0.76`:        化学モデルなしで実行する場合のシミュレーションの水素比。
  * `ν0::Real=1.44e9`:           観測周波数 $Hz$ で。
  * `dsa_model::Integer=1`:      拡散衝撃加速モデル。値は `0...4` を取ります。次のセクションを参照してください。
  * `K_ep::Real=0.01`:           CR陽子と電子エネルギー加速の比率。
  * `show_progress::Bool=false`: trueに設定すると進行状況バーが有効になります。

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
