```
speciescontribution(::Type{C}, N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Binary}, sp::T, f, args...; replicates=999, kwargs...) where {C <: PermutationConstraint, T}
```

種 `sp` の `f(N, args...; kwargs...)` への寄与を返します。これは [Saavedra2011Strong](@citet) に基づいています。具体的には、この関数は種特異的な [`nullmodel`](@ref) を生成し、その後、種 `sp` の相互作用がヌルモデルの確率に従ってランダムに再描画されたネットワークのコピーを *インプレース* で更新します。

一般性のために、関数 `f` は位置引数とキーワード引数の両方を受け入れることができます。

種のスコアへの寄与は次のように定義されます。

$$
\frac{f(N)-\mu_f}{\sigma_f}
$$

ここで、μ と σ はそれぞれランダム化されたネットワーク上の測定値 `f` の平均と標準偏差です。

ヌルモデルの下で生成されたネットワークが有益であることを保証するために、ランダム化されたネットワークにおける `sp` の相互作用の数を元のネットワークにおける `sp` の相互作用の数と等しく制約します。

###### 参考文献

[Saavedra2011Strong](@citet*)
