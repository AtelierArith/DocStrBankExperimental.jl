```
M_Boson(Hsys, tier, Bath, parity=EVEN; threshold=0.0, verbose=true)
```

ボソン型HEOMリウビリアンスーパーオペレーター行列を生成します

# パラメータ

  * `Hsys` : 時間に依存しない系のハミルトニアンまたはリウビリアン
  * `tier::Int` : ボソニックバスのティア（カットオフレベル）
  * `Bath::Vector{BosonBath}` : 異なるボソニックバスのオブジェクト
  * `parity::AbstractParity` : HEOMLSが作用する演算子のパリティラベル（通常は`EVEN`、フェルミオン系のスペクトルを計算する場合のみ`ODD`に設定）。
  * `threshold::Real` : 重要度の閾値（参照[1]を参照）。デフォルトは`0.0`。
  * `verbose::Bool` : プロセス中に詳細な出力と進行状況バーを表示するかどうか。デフォルトは`true`。

パリティは、システムにフェルミオン系が含まれていて、そのスペクトル（状態密度）を計算する必要がある場合にのみ`ODD`として設定する必要があることに注意してください。

[1] [Phys. Rev. B 88, 235426 (2013)](https://doi.org/10.1103/PhysRevB.88.235426)
