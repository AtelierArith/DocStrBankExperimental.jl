```
compute_tangent_hypergraph(M::Matrix{<:SemiRing}, P::Vector{<:SemiRing}, n::Integer)
compute_tangent_hypergraph(H::Matrix{<:SemiRing}, A::Vector{Vector{Int64}},  P::Vector{<:SemiRing}, n::Integer) 
compute_tangent_hypergraph(M::Matrix{<:Number}, P::Vector{<:Number}, n::Integer, semiring=:max)
compute_tangent_hypergraph(H::Matrix{<:Number}, A::Vector{Vector{Int64}},  P::Vector{<:Number}, n::Integer, semiring=:max)
```

点 `P` の接線指向ハイパーグラフを、その生成子または不等式 `M` によって指定された熱帯円錐内で計算します（`M` が `n` 列または `2n` 列で構成されているかによって違いがあります）またはセクター `A` を持つ半空間 `H` によって指定されます。ハイパーグラフの頂点の数、そのハイパエッジ、そして `M` が不等式または半空間によって指定された場合には、ハイパエッジに関連するアクティブな不等式または半空間を返します。ハイパーグラフの頂点は1から始まるラベルが付けられますが、TPLibでは0から始まるラベルが付けられます。

# 参考文献

[1] X. Allamigeon. 静的解析によるメモリ操作の抽象解釈 – 熱帯多面体のアルゴリズムと抽象解釈への応用。博士論文。

[2] X. Allamigeon, S. Gaubert, E. Goubault. 指向ハイパーグラフを用いた熱帯多面体の頂点の計算。離散および計算幾何学, 49(2):247–279, 2013. E-print arXiv:0904.3436v4.
