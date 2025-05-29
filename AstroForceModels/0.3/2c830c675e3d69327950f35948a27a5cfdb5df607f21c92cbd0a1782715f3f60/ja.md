```
third_body_accel(u::AbstractArray, μ_body::Number, body_pos::AbstractArray, h::Number) -> SVector{3}{Number}
```

3体からの加速度を点質量として計算する

中心体も第三体によって作用を受けているため、軌道上の宇宙船𝐴に対する体𝐵の加速度は、中心体に作用しない力の一部です。

```
            a = ∇UB(rA) - ∇UB(rC)
```

# 引数

  * `u::AbstractArray`: 中心体の慣性系における宇宙船の現在の状態。
  * `μ_body`: 第三体の重力パラメータ。
  * `body_pos::AbstractArray`: 中心体の慣性系における第三体の現在の位置。

# 戻り値

  * `SVector{3}{Number}`: 第三体からの慣性加速度

```
