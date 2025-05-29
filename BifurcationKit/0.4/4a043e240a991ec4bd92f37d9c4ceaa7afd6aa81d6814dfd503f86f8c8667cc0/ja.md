```julia
struct ContIterable{Tkind<:BifurcationKit.AbstractContinuationKind, Tprob, Talg, T, S, E, TnormC, Tfinalisesolution, TcallbackN, Tevent} <: BifurcationKit.AbstractContinuationIterable{Tkind<:BifurcationKit.AbstractContinuationKind}
```

継続イテレータを定義します。これにより、例えば次のようにすることができます：

```
iter = ContIterable(prob, alg, opts; kwargs...)
for state in iter
    println("継続ステップ = ", state.step)
end
```

詳細情報は[ウェブサイト](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/iterator/)で入手できます。

# 有用な関数

  * `setparam(iter, p::Real)` レンズ `iter.prob.lens` のパラメータを `p` に設定します
  * `is_event_active(iter)` イベント検出がアクティブかどうか
  * `compute_eigenelements(iter)` 固有要素を計算するかどうか
  * `save_eigenvectors(iter)` 固有ベクトルを保存するかどうか
  * `getparams(iter)` 継続パラメータの完全なリストを取得します
  * `isindomain(iter, p)` `p` がドメイン [p*min, p*max] にあるかどうか。（[`ContinuationPar`](@ref)を参照）
  * `is_on_boundary(iter, p)` `p` が {p*min, p*max} にあるかどうか
