```
初期化(turbulence::KOmegaLKE, model::Physics{T,F,M,Tu,E,D,BI}, mdotf, peqn, config
) where {T,F,M,Tu,E,D,BI}
```

乱流輸送方程の初期化。

### 入力

  * `turbulence` – 乱流モデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `mdtof`  – 面質量流量。
  * `peqn`   – 圧力方程式。
  * `config` – ユーザーによって定義された構成構造体で、ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されています。

### 出力

  * `KOmegaLKEModel(       turbulence,       k_eqn,       ω_eqn,       kl_eqn,       nueffkLS,       nueffkS,       nueffωS,       nuL,       nuts,       Ω,       γ,       fv,       normU,       Reυ,       ∇k,       ∇ω,        state   )`  – 乱流モデル構造体。
