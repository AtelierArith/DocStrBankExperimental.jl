```
log(G::AbstractLieGroup, g, h)
log!(G::AbstractLieGroup, X, g, h)
```

リーベ群の対数写像 $\log_g: \mathcal G → \mathfrak g$ を計算します。ここで、$\mathfrak g$ は $\mathcal G$ の [`LieAlgebra`](@ref) を示します。これは次のように与えられます。

$$
\log_g h = \log_{\mathcal G}(g^{-1}∘h)
$$

ここで、$\log_{\mathcal G}$ は [Lie group logarithmic function](@ref log(::AbstractLieGroup, :Any)) を示します。この計算は `X` のインプレースで実行できます。

!!! info "命名規則"
    通常「対数」と呼ばれる少なくとも2つの異なるオブジェクトを区別する必要があります。

      * [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/) の [(Riemannian) logarithmic map](@extref `Base.log-Tuple{AbstractManifold, Any, Any}`) `log(M, p, X)`
      * (左/右/双対不変) カルタン-ショウテン (擬似) メトリックのための指数写像 `exp(G, g, X)`、これはこのパッケージ内でデフォルトとして使用されます
      * (行列/リーベ群) 指数関数 `exp(G, g)` は、ここでの $g$ が単位元である場合、前のものと一致します。

