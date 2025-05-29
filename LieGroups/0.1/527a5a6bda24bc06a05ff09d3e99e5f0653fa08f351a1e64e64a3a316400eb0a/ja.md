```
exp(G::AbstractLieGroup, X::T)
exp!(G::AbstractLieGroup, g, X)
```

リーベ群の指数関数を計算します

$$
\exp_{\mathcal G}: \mathfrak g → \mathcal G,\qquad \exp_{\mathcal G}(X) = γ_X(1),
$$

ここで、$γ_X$は初期値問題の唯一の解です

$$
γ(0) = \mathrm{e}, \quad γ'(s) = γ(s)⋅X.
$$

詳細は [HilgertNeeb:2012; Definition 9.2.2](@cite) を参照してください。行列リーベ群においては、これは [行列指数関数](https://en.wikipedia.org/wiki/Matrix_exponential) と同じです。

計算は `g` のインプレースで実行できます。

!!! info "命名規則"
    「指数」と呼ばれる少なくとも2つの異なるオブジェクトを区別する必要があります

      * [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/) からの [(リーマン) 指数写像](@extref `Base.exp-Tuple{AbstractManifold, Any, Any}`) `exp(M, p, X)`。これは `exp(base_manifold(G), p, X)` を使用してここにアクセスできます
      * (左/右/双対不変) カルタン-ショウテン (擬似) メトリックのための指数写像 `exp(G, g, X)`、これはこのパッケージ内でデフォルトとして使用されます
      * (行列/リーベ群) 指数関数 `exp(G, g)` は、ここで `g` が単位元である場合に前のものと一致します。

