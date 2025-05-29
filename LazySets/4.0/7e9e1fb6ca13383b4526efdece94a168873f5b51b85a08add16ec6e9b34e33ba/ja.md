```
chebyshev_center_radius(P::LazySet;
                        [backend]=default_polyhedra_backend(P),
                        [solver]=default_lp_solver_polyhedra(eltype(P); presolve=true))
```

ポリトピック集合の[チェビシェフ中心](https://en.wikipedia.org/wiki/Chebyshev_center)と対応する半径を計算します。

### 入力

  * `P`       – ポリトピック集合
  * `backend` – （オプション; デフォルト: `default_polyhedra_backend(P)`）ポリヘドラ計算のためのバックエンド
  * `solver`  – （オプション; デフォルト: `default_lp_solver_polyhedra(N; presolve=true)`）`Polyhedra`に渡されるLPソルバー

### 出力

ペア `(c, r)` で、`c` は `P` のチェビシェフ中心、`r` は `c` を中心とした `P` に囲まれた最大のユークリッド球の半径です。

### 注意事項

チェビシェフ中心は `P` に囲まれた最大のユークリッド球の中心です。一般に、そのような球の中心は一意ではありませんが、半径は一意です。

### アルゴリズム

`Polyhedra.chebyshevcenter` を呼び出します。
