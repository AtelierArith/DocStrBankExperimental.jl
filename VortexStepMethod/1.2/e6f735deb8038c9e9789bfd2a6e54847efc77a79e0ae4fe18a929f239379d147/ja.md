```
linearize(solver::Solver, body_aero::BodyAerodynamics, wing::RamAirWing, y::Vector{T}; 
    theta_idxs=1:4, delta_idxs=nothing, va_idxs=nothing, omega_idxs=nothing, kwargs...) where T
```

運用点周りのラムエアウィングのヤコビ行列を有限差分を用いて計算します。

# 引数

  * `solver`: VSMソルバーインスタンス（初期化されている必要があります）
  * `body_aero`: 空力ボディの表現
  * `wing`: 線形化するラムエアウィングモデル
  * `y`: 運用点での入力ベクトル、制御角度と速度の組み合わせを含む

# キーワード引数

  * `theta_idxs`: 入力ベクトルにおけるねじれ角のインデックス（デフォルト: 1:4）
  * `delta_idxs`: 後縁偏向角のインデックス（デフォルト: nothing）
  * `va_idxs`: 速度成分 `[vx, vy, vz]` のインデックス（デフォルト: nothing）
  * `omega_idxs`: 角速度成分 `[ωx, ωy, ωz]` のインデックス（デフォルト: nothing）
  * `kwargs...`: `solve!` 関数に渡される追加の引数

# 戻り値

  * `jac`: ヤコビ行列 (∂outputs/∂inputs)
  * `results`: 運用点での出力ベクトル [Fx, Fy, Fz, Mx, My, Mz, group_moments...]

# 例

```julia
# ウィングとソルバーを初期化
wing = RamAirWing("path/to/body.obj", "path/to/foil.dat")
body_aero = BodyAerodynamics([wing])
solver = Solver(body_aero)

# 4つの制御角度、速度、角速度を持つ運用点を定義
y_op = [zeros(4);        # 4つのねじれ制御角度 (rad)
       [15.0, 0.0, 0.0]; # 速度ベクトル (m/s)
       zeros(3)]         # 角速度 (rad/s)

# ヤコビ行列を計算
jac, results = linearize(
    solver, body_aero, wing, y_op;
    theta_idxs=1:4,      # ねじれ角
    va_idxs=5:7,         # 速度成分
    omega_idxs=8:10      # 角速度
)
```
