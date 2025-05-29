```
intersection(P1::Union{VPolygon, VPolytope}, P2::Union{VPolygon, VPolytope};
             [backend]=nothing, [prunefunc]=nothing)
```

2つのポリトープの交差を頂点表現で計算します。

### 入力

  * `P1`        – 頂点表現のポリトープ
  * `P2`        – 頂点表現のポリトープ
  * `backend`   – (オプション、デフォルト: `nothing`) 多面体計算のためのバックエンド
  * `prunefunc` – (オプション、デフォルト: `nothing`) 結果の頂点をプルーニングするための関数

### 出力

`VPolytope`。

### 注意事項

`prunefunc`が`nothing`の場合、この実装はそれを`(X -> removevredundancy!(X; tol=_ztol(eltype(P1))))`に設定します。
