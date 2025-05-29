```
RDPG(N::BinaryNetwork; rank::Integer=3)
```

バイナリネットワーク `N` が与えられると、`RDPG(N)` は同じ数の種を持つ確率的ネットワークを返します。ここで、すべての相互作用は、ネットワーク `N` の RDPG 空間における種の表現のドット積に等しい確率で発生します。

2つの空間 `Left * Right` の行列乗算によって得られるペアワイズドット積は、数値的および理論的な理由から 0 と 1 の間に制約されることが保証されていないため、エントリを `[0,1]` の範囲に制限します。

#### 参考文献

Dalla Riva, G.V. and Stouffer, D.B., 2016. Exploring the evolutionary signature of food webs' backbones using functional traits. Oikos, 125(4), pp.446-456. https://doi.org/10.1111/oik.02305
