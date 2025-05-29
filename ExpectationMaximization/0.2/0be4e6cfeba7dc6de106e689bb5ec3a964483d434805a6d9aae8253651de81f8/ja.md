```
fit_mle(mix::MixtureModel, y::AbstractVecOrMat, weights...; method = ClassicEM(), display=:none, maxiter=1000, atol=1e-3, rtol=nothing, robust=false, infos=false)
```

期待値最大化（EM）アルゴリズムを使用して、i.i.d サンプル `y` を用いて混合モデルの対数尤度を最大化します。`mix` 入力は EM アルゴリズムを初期化するために使用される混合モデルです。

  * `weights` が提供されると、EM の加重バージョンを計算します。（混合の混合をフィッティングするのに便利です）
  * `method` は使用されるアルゴリズムを決定します。
  * `infos = true` はアルゴリズムに関する情報（収束したか、反復回数、対数尤度）を含む `Dict` を返します。
  * `robust = true` は（対数）尤度が `-∞` または `∞` にオーバーフローするのを防ぎます。
  * `atol` はアルゴリズムの収束を決定する基準です。2つの反復 `i` と `i+1` の間の対数尤度の差が `atol` より小さい場合、すなわち `|ℓ⁽ⁱ⁺¹⁾ - ℓ⁽ⁱ⁾|<atol` の場合、アルゴリズムは停止します。
  * `rtol` は収束のための相対許容誤差で、`|ℓ⁽ⁱ⁺¹⁾ - ℓ⁽ⁱ⁾|<rtol*(|ℓ⁽ⁱ⁺¹⁾| + |ℓ⁽ⁱ⁾|)/2` （`rtol` が `nothing` であるかどうかはチェックしません）
  * `display` の値は `:none`、 `:iter`、 `:final` で、各反復の対数尤度の進行状況を表示するか、最終的なものだけを表示します `:final` です。
