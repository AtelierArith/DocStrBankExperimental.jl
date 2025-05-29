```
初期化(turbulence::Smagorinsky, model::Physics{T,F,M,Tu,E,D,BI}, mdotf, peqn, config
) where {T,F,M,Tu,E,D,BI}
```

乱流輸送方程の初期化。

### 入力

  * `turbulence` – 乱流モデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `mdtof`  – 面質量流量。
  * `peqn`   – 圧力方程式。
  * `config` – ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されたユーザー定義の構成構造。

### 出力

  * `SmagorinskyModel(       turbulence,        Δ,        magS,        ModelState((), false)   )`  – 乱流モデル構造。
