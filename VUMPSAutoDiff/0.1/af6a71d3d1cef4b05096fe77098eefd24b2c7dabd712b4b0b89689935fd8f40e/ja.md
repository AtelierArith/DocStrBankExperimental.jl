```
AbstractLinearMap
```

転送行列計算で使用される線形マップを表す抽象型。サブタイプは、以下の必須メソッドを実装する必要があります：

1. **ベクトル空間の定義**：

      * `right_space(TM)`: 右環境計算のためのベクトル空間を返します
      * `left_space(TM)`: 左環境計算のためのベクトル空間を返します
2. **転送操作**：

      * `left_transfer(TM, v)`: 左環境ベクトル `v` に転送行列を適用します
      * `right_transfer(TM, v)`: 右環境ベクトル `v` に転送行列を適用します
3. **自動微分**：

      * `ChainRulesCore.rrule` コンストラクタ: 勾配伝播ルールを定義します

具体的な実装は以下で見ることができます：

  * `MPSMPSTransferMatrix` (MPS-MPSシステム)
  * `MPSMPOMPSTransferMatrix` (MPS-MPO-MPSシステム)
  * `ACMap` (VUMPS反復におけるACの線形マップ)

サブタイプは、環境テンソルを通じて前方計算と後方勾配伝播の両方を可能にするために、コア転送操作を実装する必要があります。
