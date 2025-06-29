```
determinism(R[; lmin=2, theiler])
```

再帰行列 `R` の決定論を計算します：

## 説明

決定論は次のように計算されます：

$$
DET = \frac{\sum_{l=lmin}{l P(l)}}{\sum_{l=1}{l P(l)}} =
\frac{\sum_{l=lmin}{l P(l)}}{\sum R}
$$

ここで $l$ は行列の対角線の長さを表し、$P(l)$ は長さが $l$ に等しい線の数です。

`lmin` はデフォルトで 2 に設定されており、この計算はタイラーウィンドウ内のすべての点を除外します（デフォルト値とキーワード引数 `theiler` の使用については [`rqa`](@ref) を参照してください）。
