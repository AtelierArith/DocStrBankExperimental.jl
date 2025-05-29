```
energy::SensibleEnthalpyModel, model::Physics{T1,F,M,Tu,E,D,BI}, prev, mdotf, rho, mueff, time, config
) where {T1,F,M,Tu,E,D,BI,E1}
```

エネルギー輸送方程式を実行します。

### 入力

  * `energy` – エネルギーモデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `prev`   – 前のエネルギーセルの値。
  * `mdtof`  – 面質量流量。
  * `rho`    – 密度スカラー場。
  * `mueff`  – 有効粘度面スカラー場。
  * `time`   –
  * `config` – ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されたユーザー定義の構成構造。
