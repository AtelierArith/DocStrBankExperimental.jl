```
pressure_f(env, krs, freq, r, zs, zr; t0 = 0.1, max_modes = Inf)

ペケリスモデルの圧力場を計算します。

# 引数
- `env::PekerisUnderwaterEnv`: 水中環境。
- `krs::Vector{Real}`: 水平波数。
- `freq::Real`: 信号の周波数。
- `r::Real`: 範囲。
- `zs::Real`: ソースの深さ。
- `zr::Real`: 受信機の深さ。
- `t0::Real=0.1`: 時間オフセット。
- `max_modes::Int=Inf`: 使用する最大モード数。

# 戻り値
- `Complex{Real}`: 圧力場。
```
