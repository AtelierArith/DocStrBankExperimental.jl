```
kernel_eigs(xs::AbstractArray, ϵ::Number, nev::Integer, σ::Number,
            boundary_weights::Vector; kernel::Symbol=:SquaredExponential,
            zero_mean = false, check = 1)
```

不変の固有値問題を解きます。これはレイリー商によって与えられます。

> `min_c (‖GKc‖² + ‖Kc‖²_bd + ϵ‖c‖²_k)/‖Kc‖²`


ここで

  * `‖GKc‖²` は不変性（および可能な非ゼロ平均）をペナルティするノルムです。
  * `‖Kc‖²_bd` は境界違反をペナルティするノルムです。
  * `‖c‖²_k` はスムージングカーネルノルムです。
  * `‖Kc‖²` は点の ℓ² ノルムです。

固有値問題は `Arpack.jl` を介して解決されます。

引数:

  * `xs`: サイズ d × 2N の補間点で、xs[:, N+1:2N] = F.(xs[:, 1:N]) です。
  * `ϵ`: 正則化の量
  * `nev`: 見つける固有値の数
  * `σ`: カーネル幅
  * `boundary_weights`: 境界重みベクトルで、|k(x)| << 1 となる点 `x` で正で O(1) であるべきです。
  * `kernel`: 補間するカーネルのタイプ（`KernelLabel` を参照）
  * `zero_mean = false`: `k` にゼロ平均を持つことを促す制約を追加するには true に設定します。`xs` が不変集合上でサンプリングされ、boundary_weights=0 の場合に便利です。
  * `check = 1`: `Arpack.eigs` を参照してください。1 の場合、収束したすべての固有ベクトルと固有値を返します。0 の場合は、代わりにエラーをスローします。

出力:

  * `λs`: 固有値
  * `vs`: 固有ベクトル
  * `k`: カーネルラベル。`set_c!(k, vs[:,n])` を使用して `n` 番目の固有ベクトルを `k` にロードします。デフォルトでは、`k` は最も低い次数の固有ベクトルを格納します。
