```
init(::ParaReal.Problem,
     ::ParaReal.Algorithm;
     kwargs...)
```

指定された `workers` のワーカー ID で最終的に実行されるパイプラインを初期化します。パイプラインステージを実行するタスクは開始しません。

[`Pipeline`](@ref) を返します。

# キーワード引数

  * `schedule::ParaReal.Schedule = ProcessesSchedule()`: ステージを実行するタスクをどのように分散/スケジュールするかを指定します
  * `maxiters = 10`: ニュートンの洗練の最大数、`k <= K = maxiters`
  * `nconverged = 2`: 有意な変化なしに連続する洗練の数; 収束について推論するために使用されます（詳細は以下に記載）；収束チェックを完全に無効にするには `typemax(Int)` に設定します
  * `rtol::Float64 = size(iv, 1) * eps()`: 相対誤差、ここで `iv = initial_value(prob.p)`; 収束について推論するために使用されます（詳細は以下に記載）
  * `atol::Float64 = 0.0`: 絶対誤差; 収束について推論するために使用されます（詳細は以下に記載）
  * `logger = nothing`: パイプラインステージのメッセージをログする場所。`nothing` の場合、各ワーカーで `current_logger()` を使用します。エラーは `with_logger(logger) do ... end` の外で再スローされ、すなわちグローバルロガーによって処理されます。
  * `warmupc::Bool = true`: `csolve` の JIT ウォームアップを制御します。cf. [`Algorithm`](@ref)
  * `warmupf::Bool = false`: `fsolve` の JIT ウォームアップを制御します。cf. [`Algorithm`](@ref)

# 収束

洗練 `Uᵏ` が有意な変化を示さなかった場合は

```
dist(Uᵏ, Uᵏ⁻¹) <= max(atol, max(norm(Uᵏ), norm(Uᵏ⁻¹)) * rtol)
```

を使用します [`dist`](@ref) と `LinearAlgebra.norm`。`norm(Uᵏ)` の計算が高価である可能性があるため、その値はイテレーション間でキャッシュされます。それ以外は、これは本質的に `isapprox` のように機能します。

ステージ `n` は、次の条件を満たす場合に収束したと見なされます。

1. `>= nconverged` 回の連続した洗練が有意な変化を示さなかった場合、かつ
2. 前のステージ `n-1` が最大で 1 回の洗練を計算する必要があった場合、すなわち `k(n) >= k(n-1) - 1`。

第二の基準により、有意な変化なしに `> nconverged` 回の洗練が計算されている可能性があります。

収束チェックを無効にするには `nconverged` を `typemax(Int)` に設定します。その場合、`dist` も `norm` も計算されず、カスタムソリューションタイプのための特別なメソッドも必要ありません。
