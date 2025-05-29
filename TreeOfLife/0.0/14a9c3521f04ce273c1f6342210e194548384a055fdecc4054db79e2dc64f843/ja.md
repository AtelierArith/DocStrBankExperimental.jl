```
getphylodiv(tree::ChronoTree, tipset; keeproot::Bool=false)
```

与えられた木のティップのセットの系統的多様性（PD）を計算します。すなわち、セットから生成される部分木の枝の長さの合計です。

引数 `keeproot` は、元の根ノードが部分木に含まれる必要があるかどうかを制御します。デフォルトでは `false` に設定されています。
