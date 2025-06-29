```
transition_matrix(s::AbstractAxisymmetricShape{T, CT}, λ; ...) where {T, CT}
```

軸対称形状の遷移行列を計算するためのメイン関数。

パラメータ：

  * `s`: 軸対称形状
  * `λ`: 波長

キーワード引数：

  * `threshold`: 収束閾値、デフォルトは `0.0001`
  * `ndgs`: 度ごとの離散ガウス積分点の数、デフォルトは `4`
  * `routine_generator`: 収束ルーチンを生成する関数、デフォルトは `routine_mishchenko`
  * `nₛₜₐᵣₜ`: 切断次数の初期値、デフォルトは `0` で、実際の値は次の式を使用して自動的に計算されます：

$$
n_{\text{start}} = \max(4, \lceil kr_{\max} + 4.05 \sqrt[3]{kr_{\max}} \rceil)
$$

  * `Ngₛₜₐᵣₜ`: 離散ガウス積分点の初期数、デフォルトは `nₛₜₐᵣₜ * ndgs`
  * `nₘₐₓ_only`: `nₘₐₓ` の収束のみをチェックするか、デフォルトは `false` で、`nₘₐₓ` と `Ng` の両方の収束がチェックされます
  * `full`: 各イテレーションで全体の遷移行列を計算するか、デフォルトは `false` で、`m=m′=0` ブロックのみが計算されます
  * `reuse`: 前のイテレーションのキャッシュを再利用するか、デフォルトは `true`
  * `maxiter`: 最大イテレーション数、デフォルトは `20`
  * `zerofn`: 数値積分に使用される型を定義する関数、デフォルトは `() -> zero(CT)` で、ここで `CT` は形状によって定義されます
