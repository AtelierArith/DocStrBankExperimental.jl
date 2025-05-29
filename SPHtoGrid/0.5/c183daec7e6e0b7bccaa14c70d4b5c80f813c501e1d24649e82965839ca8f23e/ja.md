```
analytic_synchrotron(P_cgs::Array{<:Real}, B_cgs::Array{<:Real}, 
                     Mach::Array{<:Real}, θ_B::Union{Nothing,Array{<:Real}}=nothing;
                     dsa_model::Union{Integer,AbstractShockAccelerationEfficiency}=1, 
                     ν0::Real=1.4e9,
                     K_ep::Real=0.01, CR_Emin::Real=1.0,
                     spectrum::Union{Nothing,Function}=nothing,
                     integrate_pitch_angle::Bool=true,
                     polarisation::Bool=false,
                     show_progress::Bool=false)
```

電子のスペクトルからの解析的シンクロトロン放射を、分布関数を明示的に積分することによって計算します。スペクトルに対する積分は1に正規化されている必要があります。相対論的電子の総エネルギー密度は、DSAモデルを用いて得られたCRと熱圧の比によって与えられ、[Pfrommer et. al. (2017)](https://ui.adsabs.harvard.edu/abs/2017MNRAS.465.4500P/abstract)のようにXcrを計算します。

シンクロトロン放射強度 `j_nu` を単位 `[erg/s/Hz/cm^3]` で返します。

# 引数

  * `P_cgs::Array{<:Real}`:   熱エネルギー密度 `erg/cm^3` で。
  * `B_cgs::Array{<:Real}`:   ガウス単位の磁場。
  * `Mach::Array{<:Real}`:    マッハ数。
  * `θ_B::Union{Nothing,Array{<:Real}}=nothing`: 衝撃の傾斜（オプション）。

## キーワード引数

  * `ν0::Real=1.4e9`:           観測周波数 `Hz` で。
  * `dsa_model`:      拡散衝撃加速モデル。値は `0...4` またはカスタムモデルを取ります。次のセクションを参照してください。
  * `K_ep::Real=0.01`:           CR陽子と電子のエネルギー加速の比。
  * `CR_Emin::Real=1`:           CR電子集団の注入エネルギー `GeV` で。
  * `spectrum::Union{Nothing,Function}=nothing`: スペクトル関数。積分が1になるように正規化されている必要があります。
  * `integrate_pitch_angle::Bool=true`: 計算コストを削減するためにピッチ角の積分を避けるオプション。
  * `polarisation::Bool=false`: 総強度の代わりに偏光放射を計算したい場合は `true` に設定します。
  * `show_progress::Bool=false`: `true` に設定すると進行状況バーが有効になります。

## DSAモデル

自己定義の `AbstractShockAccelerationEfficiency`（詳細は [DiffusiveShockAccelerationModels.jl](https://github.com/LudwigBoess/DiffusiveShockAccelerationModels.jl) を参照！）または数値値を入力として取ります。数値値は次のように対応します：

  * `0`: [Kang et. al. (2007)](https://ui.adsabs.harvard.edu/abs/2007ApJ...669..729K/abstract)
  * `1`: [Kang & Ryu (2013)](https://ui.adsabs.harvard.edu/abs/2013ApJ...764...95K/abstract)
  * `2`: [Ryu et. al. (2019)](https://ui.adsabs.harvard.edu/abs/2019ApJ...883...60R/abstract)
  * `3`: [Caprioli & Spitkovsky (2014)](https://ui.adsabs.harvard.edu/abs/2014ApJ...783...91C/abstract)
  * `4`: [Pfrommer et. al. (2006)](https://ui.adsabs.harvard.edu/abs/2006MNRAS.367..113P/abstract)

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`

```
