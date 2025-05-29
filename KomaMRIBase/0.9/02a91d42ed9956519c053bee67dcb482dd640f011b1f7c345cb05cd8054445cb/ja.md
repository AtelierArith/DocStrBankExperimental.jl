```
x, y, z = get_spin_coords(motionset, x, y, z, t)
```

各スピンの位置を一連の任意の時間瞬間で計算します。すなわち、シミュレーションの時間ステップです。各次元（x, y, z）について、出力行列は $N_{	{spins}}$ 行と `length(t)` 列を持ちます。

# 引数

  * `motion`: (`::Union{NoMotion, MotionList{T<:Real}}`) 幽霊運動
  * `x`: (`::AbstractVector{T<:Real}`, `[m]`) スピンのx位置ベクトル
  * `y`: (`::AbstractVector{T<:Real}`, `[m]`) スピンのy位置ベクトル
  * `z`: (`::AbstractVector{T<:Real}`, `[m]`) スピンのz位置ベクトル
  * `t`: 時間瞬間の水平配列

# 戻り値

  * `x, y, z`: (`::Tuple{AbstractArray, AbstractArray, AbstractArray}`) 時間にわたるスピンの位置
