```
getKLdivergence(meta, VDF; species="proton")
getKLdivergence(meta, vcellids, vcellf; species="proton")
```

KLダイバージェンス ∫ f*log(f/g)dv を取得します。ここで `f` は Vlasiator からの VDF で、`g` は `f` と同じ密度を生成する解析的マクスウェリアン分布です。値は [0, +∞] の範囲で、0 は完璧なマクスウェリアンを意味します。通常、値は非常に小さいです。あるいは、元の `vcellids` と `vcellf` を直接渡すこともできます。
