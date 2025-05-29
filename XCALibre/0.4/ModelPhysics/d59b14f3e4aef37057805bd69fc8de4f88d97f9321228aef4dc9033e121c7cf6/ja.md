```
turbulence!(les::SmagorinskyModel, model::Physics{T,F,M,Tu,E,D,BI}, S, S2, prev, time, config
) where {T,F,M,Tu<:AbstractTurbulenceModel,E,D,BI}
```

乱流モデルの輸送方程式を実行します。

### 入力

  * `les::SmagorinskyModel` – Smagorinsky LES 乱流モデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `S`   – ひずみ率テンソル。
  * `S2`  – ひずみ率の大きさの二乗。
  * `prev`  – 前のフィールド。
  * `time`   –
  * `config` – ユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されています。
