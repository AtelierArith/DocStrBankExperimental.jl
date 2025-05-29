```
   GDE, GDR, _ = GridEn(Sig)
```

データ系列（`Sig`）から推定されたグリッド分布エントロピー（`GDE`）とグリッド分布率（`GDR`）を返します。デフォルトのパラメータを使用します：グリッド粗粒化 = 3、時間遅延 = 1、対数 = 基数 2

```
   GDE, GDR, PIx, GIx, SIx, AIx = GridEn(Sig)
```

GDEとGDRに加えて、GridEnはデータ系列（`Sig`）に対して推定された以下の指標を返します。デフォルトのパラメータを使用します： [`PIx`] - 同一線（LI）以下の点の割合 [`GIx`] - LI以上の点の距離の割合 [`SIx`] - LI以上の点の位相角の比（LIに対して） [`AIx`] - LI以上の点のセクターの累積面積の比

```
   GDE, GDR, ..., = GridEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=3, tau::Int=1, Logx::Real=exp(1), Plotx::Bool=false)
```

指定された「キーワード」引数を使用してデータ系列（`Sig`）から推定されたグリッド分布エントロピー（`GDE`）を返します：

# 引数：

`m`     - グリッド粗粒化（m x m セクター）、整数 > 1 

`tau`   - 時間遅延、正の整数    

`Logx`  - 対数の基数、正のスカラー 

`Plotx` - Plotx == true の場合、グリッド点分布のグリッドポワレ図と二変量ヒストグラムを返します（デフォルト：false）  

# 参照： `PhasEn`, `CoSiEn`, `SlopEn`, `BubbEn`, `MSEn`

# 参考文献：

```
   [1] Chang Yan, et al.,
           "Novel gridded descriptors of poincaré plot for analyzing 
           heartbeat interval time-series." 
           Computers in biology and medicine 
           109 (2019): 280-289.

   [2] Chang Yan, et al. 
           "Area asymmetry of heart rate variability signal." 
           Biomedical engineering online 
           16.1 (2017): 1-14.

   [3] Alberto Porta, et al.,
           "Temporal asymmetries of short-term heart period variability 
           are linked to autonomic regulation." 
           American Journal of Physiology-Regulatory, Integrative and 
           Comparative Physiology 
           295.2 (2008): R550-R557.

   [4] C.K. Karmakar, A.H. Khandoker and M. Palaniswami,
           "Phase asymmetry of heart rate variability signal." 
           Physiological measurement 
           36.2 (2015): 303.
```
