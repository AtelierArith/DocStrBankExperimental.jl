```
lp(N::T) where {T<:AbstractEcologicalNetwork}
```

ラベル伝播を使用してネットワークのモジュラー構造の最初の近似を生成します。これは通常、BRIM（`brim`）メソッドに続きます。このメソッドは大規模なグラフに対してより良いパフォーマンスを発揮するとされていますが、小規模なグラフではそれとBRIMの変種との間に違いをほとんど観察しませんでした。

#### 参考文献

Liu, X., Murata, T., 2009. Community Detection in Large-Scale Bipartite Networks, in: 2009 IEEE/WIC/ACM International Joint Conference on Web Intelligence and Intelligent Agent Technology. Institute of Electrical & Electronics Engineers (IEEE). https://doi.org/10.1109/wi-iat.2009.15
