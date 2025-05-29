```
genauxga(model::GAModel) :: GAModel 補助構造
```

与えられたモデル GAM <: GAModel に対して、フィットネススコアを計算するための補助的なスクラッチスペースを生成します。モデル = GAM(G1,G2) aux = genauxga(model) の目的は、新しいクリーチャーのフィットネスを計算するたびにメモリを割り当てないことです。
