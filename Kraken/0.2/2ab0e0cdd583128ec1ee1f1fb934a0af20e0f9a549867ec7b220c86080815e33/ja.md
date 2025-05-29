```
find_kr(env, freq, p; n_points = 5_000, method = A42())

Pekerisモデルの水平波数を求めます。

# 引数
- `env::PekerisUnderwaterEnv`: 水中環境。
- `freq::Real`: 信号の周波数。
- `p::Vector{Real}`: Pekerisパラメータ。
- `n_points::Int=2_000`: 探索に使用するポイントの数。
- `method::NonlinearSolver=NewtonRaphson()`: 探索に使用する方法。

# 戻り値
- `Vector{Real}`: 水平波数。
```
