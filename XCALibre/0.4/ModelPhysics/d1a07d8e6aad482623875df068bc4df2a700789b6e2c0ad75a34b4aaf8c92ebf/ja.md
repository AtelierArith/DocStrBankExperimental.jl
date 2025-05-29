```
initialise(energy::SensibleEnthalpy, model::Physics{T1,F,M,Tu,E,D,BI}, mdotf, rho, peqn, config
) where {T1,F,M,Tu,E,D,BI})
```

エネルギー輸送方程式の初期化。

### 入力

  * `energy` – エネルギーモデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `mdtof`  – 面質量流量。
  * `rho`    – 密度スカラー場。
  * `peqn`   – 圧力方程式。
  * `config` – ユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されています。

### 出力

  * `SensibleEnthalpyModel`  – エネルギー方程式を含むエネルギーモデル構造体。
