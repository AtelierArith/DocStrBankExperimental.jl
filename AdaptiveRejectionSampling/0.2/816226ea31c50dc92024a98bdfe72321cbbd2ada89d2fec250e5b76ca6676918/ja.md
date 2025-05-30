RejectionSampler(f::Function, support::Tuple{Float64, Float64}, init::Tuple{Float64, Float64})     RejectionSampler(f::Function, support::Tuple{Float64, Float64}[ ,δ::Float64]) 適応型拒否サンプラーは、`support = (support[1], support[2])` でサポートされる対数凹関数からiidサンプルを取得するためのものです。 fは、サンプリングされる関数の確率密度であるか、その対数であるかのいずれかです。 後者の場合は、キーワード引数 `log=true` を使用します。 関数は、確率密度が定数まで指定できるという意味で、正規化されていない場合があります。 適応型拒否サンプリングアルゴリズムは、(d/dx)logp(init[1]) > 0 および (d/dx)logp(init[2]) < 0 となる2つの初期点 `init = init[1], init[2]` を必要とします。 これらの点は直接提供することができ（通常、モードの左側と右側の任意の点で構いません）、初期点の貪欲な探索のために範囲とデルタを指定して検索することも可能です。 `support` は `(-Inf, Inf), (-Inf, a), (b, Inf), (a,b)` の形式でなければならず、fが正の値を持つ区間を表し、他の場所ではゼロです。

代替コンストラクタは、search_range、検索内の点間の距離の値δ、および絶対値での最小/最大傾斜値を使用します。

## キーワード引数

  * `max_segments::Int = 10` : エンベロープの最大サイズ、セグメント数が少ないと拒否率は通常遅くなります
  * `max_failed_factor::Float64 = 0.001`: 単一のサンプルの拒否率がこの値を超えた場合にエラーをスローするレベル
  * `logdensity::Bool = false`: `f` が確率密度の対数であるかどうかを示す指標、正規化定数まで。
  * `search_range::Tuple{Float64,Float64} = (-10.0, 10.0)`: 初期点を検索する範囲
  * `min_slope::Float64 = 1e-6`: 初期/発見された点でのlogfの絶対値の最小傾斜
  * `max_slope::Float64 = Inf`: 初期/発見された点でのlogfの絶対値の最大傾斜
