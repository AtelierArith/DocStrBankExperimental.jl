```
mutable struct dftout
```

DFT出力構造体。持つもの

  * `crys::crystal`  結晶構造
  * `energy::Float64` 実際のDFTエネルギー、擬ポテンシャルに依存。
  * `energy_smear::Float64` スミアリングエネルギー
  * `forces::Array{Float64,2}` 力 Ryd / a.u.
  * `stress::Array{Float64,2}` 応力 Ryd / (a.u.)^3
  * `bandstruct::bandstructure` バンド構造構造体を参照
  * `hasband::Bool` このオブジェクトはバンド構造を持つか、通常は `true`
  * `hasham::Bool` 使用されていない、常に `false`
  * `prefix::String` 出力ファイルを見つけるために使用される名前の文字列。
  * `outdir::String` 直接読み込まれた
  * `tot_charge::Float64` 単位セルの電荷がゼロでない場合
  * `atomize_energy::Float64` 原子化エネルギー、非スピン偏極原子に対して相対的。
  * `nspin::Int64` スピンの数 (1 = 非スピン偏極, 2= スピン偏極)
  * `mag_tot::Float64` 総磁化  = sum*i mag*i
  * `mag_abs::Float64` 絶対磁化 = sum*i | mag*i |
