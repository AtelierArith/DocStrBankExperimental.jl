```
compute_halfspaces(M::Matrix{<:SemiRing}, n::Integer)
compute_halfspaces(M::Matrix{<:Number}, n::Integer, semiring=:max)
```

トロピカルコーンのトロピカル半空間による最小外部表現を生成セット `M` に基づいて次元 `n` で計算します。生成セットは空であってはならず、つまり `M` は空であってはなりません。現在、すべてのベクトルが有限のエントリを持つ生成セットの場合のみ処理します。戻り値はペア `(H::Matrix{<:SemiRing},A::Vector{Vector{Integer}})` であり、`H` の行はトロピカル半空間の方程式であり、`A` のベクトルは各半空間のセクターです。

# 参考文献

[1] X. Allamigeon and R.D. Katz. Minimal external representations of tropical polyhedra. Journal of Combinatorial Theory, Series A, 120(4):907–940, 2013.  Eprint arXiv:1205.6314.
