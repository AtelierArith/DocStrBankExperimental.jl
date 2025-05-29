```
TAMSD(TA::TimeAverage, order::Int, τ::Float64, N::Int)
𝔼(TA::TimeAverage; τ::Float64=1e-2, N::Int=100_000, order::Int=10)
```

時間平均平均二乗変位 (TAMSD) を計算します。

# 引数

  * `TA` : コンストラクタ `δ̄²(::StochasticProcess, T::Real, Δ::Real)` によって構築された時間平均
  * `τ` : オイラー法の時間ステップ
  * `N` : モンテカルロシミュレーションにおける粒子の数
  * `order` : ガウス-レジェンドル数値積分における項の数

# 使用法

```julia
T = 100; Δ = 1
x::StochasticProcess = ....  # 確率過程のインスタンスを定義
𝔼(δ̄²(x, T, Δ))  # TAMSDを計算
```
