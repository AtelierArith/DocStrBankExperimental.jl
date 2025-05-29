```
function initialise(
    turbulence::Laminar, model::Physics{T,F,M,Tu,E,D,BI}, mdotf, peqn, config
    ) where {T,F,M,Tu,E,D,BI}
return LaminarModel()
```

end

乱流輸送方程式の初期化。

### 入力

  * `turbulence` – 乱流モデル。
  * `model`  – ユーザーによって定義された物理モデル。
  * `mdtof`  – 面質量流量。
  * `peqn`   – 圧力方程式。
  * `config` – ソルバー、スキーム、ランタイム、およびハードウェア構造が設定されたユーザーによって定義された構成構造。

### 出力

  * `LaminarModel()`  – 乱流モデル構造。
