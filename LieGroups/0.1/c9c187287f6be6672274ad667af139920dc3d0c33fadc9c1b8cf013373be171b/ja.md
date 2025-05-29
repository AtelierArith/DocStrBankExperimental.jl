```
log(G::AbstractLieGroup, g, h)
log(G::AbstractLieGroup, g)
log(G::AbstractLieGroup, g::Identity, T)
log!(G::AbstractLieGroup, X::T, g)
```

(リー群) 対数関数 $\log_{\mathcal G}: \mathcal G → \mathfrak g$ を計算します。これは [リー群指数関数](@ref exp(::AbstractLieGroup, :Any)) の逆です。割り当てバリアントの場合、点引数が単位元であり、したがって使用される表現を提供しないときに、型 `T` を指定できます。計算は `X::T` のインプレースで行うことができ、これにより型が決定されます。

!!! info "命名規則"
    通常「対数」と呼ばれる少なくとも2つの異なるオブジェクトを区別する必要があります

      * [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/) のマップ `log(M, p, q)` である [(リーマン) 対数](@extref `Base.log-Tuple{AbstractManifold, Any, Any}`)。これは `log(base_manifold(G), p, q)` を使用してここにアクセスできます。
      * (左/右/双対不変) カルタン-ショウテン (擬似) メトリック `log(G, g, h)` の対数マップ。これはこのパッケージ内でデフォルトとして使用します。
      * 行列/リー群の対数関数 `log(G, h)` は、ここで `g` が単位元である場合に前のものと一致します。

