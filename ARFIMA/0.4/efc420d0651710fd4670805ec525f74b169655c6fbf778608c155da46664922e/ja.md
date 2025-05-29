```
arfima([rng,] N, σ, d, φ=nothing, θ=nothing) -> Xₜ
```

長さ `N` の確率過程の時系列を生成します。この過程は ARFIMA プロセスまたはそのサブクラス（例えば ARMA、AR、ARIMA など）に従います。`σ` はプロセスを生成するために使用されるホワイトノイズの標準偏差です。最初のオプション引数は `AbstractRNG` で、再現性を確立するための乱数生成器です。

`Xₜ` の生成方程式は次の通りです：

$$
\left( 1 - \sum_{i=1}^p \phi_i B^i \right)
\left( 1-B \right)^d X_t
=
\left( 1 + \sum_{i=1}^q \theta_i B^i \right) \varepsilon_t
$$

ここで $B$ はバックシフト演算子、$\varepsilon_t$ はホワイトノイズです。

この方程式は ARFIMA のすべての可能なバリアントをカプセル化しており、Julia の多重ディスパッチシステムは `d, φ, θ` の型に基づいてシミュレーションされるバリアントを決定します。

## バリアント

ARFIMA パラメータは (p, d, q) で、`p = length(φ)` および `q = length(θ)` です。`p, q` は自己回帰または移動平均の「次数」を表し、`d` は差分の「次数」を表します。`φ, θ` は `Nothing` または `SVector` の 2 種類の型を持つことができます。`Nothing` の場合、自己回帰 (φ) および移動平均 (θ) の対応する成分は行われません。それ以外の場合、静的ベクトルは単にその値を含みます。

`d` が `Nothing` の場合、差分（統合）部分は行われず、プロセスは実際には AR/MA/ARMA です。`d` が `Int` 型の場合、シミュレーションされたプロセスは実際には ARIMA であり、`d` が `AbstractFloat` の場合、プロセスは AR**F**IMA です。この場合、`d ∈ (-0.5, 0.5)` である必要があります。すべての `d, φ, θ` が `nothing` の場合、ホワイトノイズが返されます。

便利のために、関数 `arma(N, σ, φ, θ = nothing)` が提供されています。

## 例

```julia
N, σ = 10_000, 0.5
arfima(N, σ, 0.4)                                   # ARFIMA(0,d,0)
arfima(N, σ, 0.4, SVector(0.8))                     # ARFIMA(1,d,0)
arfima(N, σ, 1, SVector(0.8))                       # ARIMA(1,d,0)
arfima(N, σ, 1, SVector(0.8), SVector(1.2))         # ARIMA(1,d,1)
arfima(N, σ, 0.4, SVector(0.8), SVector(1.2))       # ARFIMA(1,d,1)
arfima(N, σ, nothing, SVector(0.8))                 # AR(1)
arfima(N, σ, nothing, nothing, SVector(1.2))        # MA(1)
arfima(N, σ, nothing, SVector(0.8), SVector(1.2))   # ARMA(1,1)
```
