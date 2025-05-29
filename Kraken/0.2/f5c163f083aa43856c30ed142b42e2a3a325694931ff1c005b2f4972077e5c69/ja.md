```
get_modal_function(env, krs, freq, zr, zs)

Pekerisモデルのモーダル関数を取得します。

# 引数
- `env::PekerisUnderwaterEnv`: 水中環境。
- `krs::Vector{Real}`: 水平波数。
- `freq::Real`: 信号の周波数。
- `zr::Real`: 受信機の深さ。
- `zs::Real`: ソースの深さ。

# 戻り値
- `Vector{Real}`: 受信機の深さでのモーダル関数。
- `Vector{Real}`: ソースの深さでのモーダル関数。
```
