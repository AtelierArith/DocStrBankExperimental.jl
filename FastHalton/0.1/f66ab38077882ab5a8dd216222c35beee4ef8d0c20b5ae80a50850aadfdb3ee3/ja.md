```
HaltonSeq(base, length, skip=5000, f=identity)
```

イテレータは、素数 `base` と `length` を指定して `Rational{Int}` の Halton シーケンスを生成し、最初の `skip` 要素をスキップします。関数 `f`（例えば `StatsFuns::norminvcdf`）を使用して、Halton の引き出しを分布からの準ランダム引き出しに変換できます。

アルゴリズムは Kolar & O'Shea (1993) に示されており、[https://doi.org/10.1016/0898-1221(93)90307-H](https://doi.org/10.1016/0898-1221(93)90307-H) では、`Vector` の `d` と `r` を使用して中間計算を追跡します。
