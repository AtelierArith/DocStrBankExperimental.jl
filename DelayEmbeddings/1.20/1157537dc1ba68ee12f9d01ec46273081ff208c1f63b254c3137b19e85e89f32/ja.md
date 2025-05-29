```
estimate_dimension(s::AbstractVector, τ::Int, γs = 1:5, method = "afnn"; kwargs...)
```

最適な時間的隣接点の数 `γ` を推定する量を計算します。この量は [`reconstruct`](@ref) または [`embed`](@ref) で使用されます。

## 説明

スカラー時系列 `s` と埋め込み遅延 `τ` が与えられたとき、埋め込まれた時系列の「最近傍」に基づいて、各 `γ ∈ γs` に対して量を計算します。

計算される量は、文字列 `method` で定義されたアルゴリズムによって異なります：

  * `"afnn"`（デフォルト）は、Caoの「平均偽最近傍」法[^Cao1997]で、最近傍間の距離の比率を提供します。この比率は、最適な `γ` の近くで `1.0` に飽和します（[`afnn`](@ref) を参照）。
  * `"fnn"` は、Kennelの「偽最近傍」法[^Kennel1992]で、次元が増加する際に「最近傍」でなくなる点の数を提供します。この数は、最適な `γ` の近くでゼロに減少します。この方法は、Kennelのアルゴリズムに必要な「許容誤差」を表すキーワード引数 `rtol` と `atol` を受け入れます（[`fnn`](@ref) を参照）。
  * `"f1nn"` は、Krakovskáの「偽第一最近傍」法[^Krakovská2015]で、次元が増加する際に「最近傍」でなくなる点のペアの比率を提供します。この数は、最適な `γ` の近くでゼロに減少します（[`f1nn`](@ref) を参照）。これはすべての中で最も劣る方法です。

`"afnn"` と `"f1nn"` は、`Cityblock()`, `Euclidean()`, `Chebyshev()` のいずれかを指定できる `metric` キーワードもサポートしています。このメトリックは、最近傍の計算（`KDTree`）とCaoの方法に必要な距離の計算の両方に使用されます（[1] の式 (2, 3) を参照）。デフォルトは `Euclidean()` です（[1] では `Chebyshev` が使用されました）。

**DynamicalSystems.jl** では、`γ` は時間的隣接点の数を表し、埋め込み次元ではないことに注意してください（`D = γ + 1`、[`embed`](@ref) も参照）。

[^Cao1997]: Liangyue Cao, [Physica D, pp. 43-50 (1997)](https://www.sciencedirect.com/science/article/pii/S0167278997001188?via%3Dihub)

[^Kennel1992]: M. Kennel *et al.*, [Phys. Review A **45**(6), (1992)](https://journals.aps.org/pra/abstract/10.1103/PhysRevA.45.3403).

[^Krakovská2015]: Anna Krakovská *et al.*, [J. Complex Sys. 932750 (2015)](https://doi.org/10.1155/2015/932750)
