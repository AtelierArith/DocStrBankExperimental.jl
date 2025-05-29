```
getmaxwellianity(meta, VDF; species="proton")
getmaxwellianity(meta, vcellids, vcellf; species="proton")
```

マクスウェリアン類似度因子を取得します -log(1/(2n) * ∫ |f - g| dv)、ここで `f` はVlasiatorからのVDFで、`g` は `f` と同じ密度を生成する解析的マクスウェリアン分布です。この値は[0, +∞]の範囲で、0は全くマクスウェリアン分布でないことを意味し、+∞は完璧なマクスウェリアン分布を意味します。あるいは、元の `vcellids` と `vcellf` を直接渡すこともできます。
