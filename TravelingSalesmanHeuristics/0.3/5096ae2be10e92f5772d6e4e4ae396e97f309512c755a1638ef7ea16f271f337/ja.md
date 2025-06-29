simulated_annealing(distmat; ...)

シミュレーテッドアニーリング戦略を使用して、閉じたツアーを返します。温度は `init_temp` から `final_temp` まで指数関数的に減衰します。タプル `(path, cost)` を返します。

### オプションのキーワード引数:

  * `steps::Int = 50n^2`: 実行するステップ数; デフォルトは 50n^2 で、n は都市の数です。
  * `num_starts::Int = 1`: シミュレーテッドアニーリングアルゴリズムを実行する回数。各回はランダムなパスから開始するか、非nullの場合は `init_path` から開始します。デフォルトは 1 です。
  * `init_temp::Real = exp(8)`: 劣ったツアーを受け入れる初期の確率を制御する初期温度。
  * `final_temp::Real = exp(-6.5)`: 劣ったツアーを受け入れる最終的な確率を制御する最終温度; より低い値はおおよそ 2-opt のより長い期間に対応します。
  * `init_path::Union{Vector{Int}, Nothing} = nothing`: アニーリングを開始するパス。`Vector{Int}` または `nothing` のいずれかです。`Vector{Int}` が与えられた場合、それが初期パスとして使用されます; そうでない場合はランダムな初期パスが使用されます。
