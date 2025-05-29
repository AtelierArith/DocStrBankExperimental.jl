```
M_Boson_Fermion(Hsys, Btier, Ftier, Bbath, Fbath, parity=EVEN; threshold=0.0, verbose=true)
```

ボソン-フェルミオン型HEOMリウビリアンスーパーオペレーター行列を生成します

# パラメータ

  * `Hsys` : 時間に依存しない系のハミルトニアンまたはリウビリアン
  * `Btier::Int` : ボソニックバスのティア（カットオフレベル）
  * `Ftier::Int` : フェルミオンバスのティア（カットオフレベル）
  * `Bbath::Vector{BosonBath}` : 異なるボソニックバスのオブジェクト
  * `Fbath::Vector{FermionBath}` : 異なるフェルミオンバスのオブジェクト
  * `parity::AbstractParity` : HEOMLSが作用する演算子のパリティラベル（通常は`EVEN`、フェルミオン系のスペクトルを計算する場合のみ`ODD`に設定）。
  * `threshold::Real` : 重要度の閾値（参照 [1, 2] を参照）。デフォルトは`0.0`。
  * `verbose::Bool` : プロセス中に詳細な出力と進行状況バーを表示するかどうか。デフォルトは`true`。

パリティは、システムにフェルミオン系が含まれていて、そのスペクトルを計算する必要がある場合にのみ`ODD`として設定する必要があることに注意してください。

[1] [Phys. Rev. B  88, 235426 (2013)](https://doi.org/10.1103/PhysRevB.88.235426) [2] [Phys. Rev. B 103, 235413 (2021)](https://doi.org/10.1103/PhysRevB.103.235413)
