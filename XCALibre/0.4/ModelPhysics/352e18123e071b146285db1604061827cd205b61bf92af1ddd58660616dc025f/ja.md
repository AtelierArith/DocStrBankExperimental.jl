turbulence!(rans::KOmegaLKEModel, model::Physics{T,F,M,Turb,E,D,BI}, S, prev, time, config     ) where {T,F,M,Turb<:AbstractTurbulenceModel,E,D,BI}

乱流モデルの輸送方程式を実行します。

### 入力

  * `rans::KOmegaLKEModel` – KOmega乱流モデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `S`   – ひずみ率テンソル。
  * `prev`  – 前のフィールド。
  * `time`   –
  * `config` – ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されたユーザーによって定義された構成構造。
