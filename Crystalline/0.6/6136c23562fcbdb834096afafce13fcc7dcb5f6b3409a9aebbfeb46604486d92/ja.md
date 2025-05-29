```
basisdim(brs::BandRepSet) --> Int
```

バンド表現セットの（線形独立部分の）次元を返します。これは、[Po, Watanabe, & Vishwanath, Nature Commun. **8**, 50 (2017)](https://doi.org/10.1038/s41467-017-00133-2) の表記法において $d^{\text{bs}} = d^{\text{ai}}$ であり、同等に、整数環上の `stack(brs)` のランクです。これは、対称性データとして見たバンド構造の展開を張る線形独立基底ベクトルの数です。
