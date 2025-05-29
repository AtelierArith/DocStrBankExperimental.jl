```
add_disturbance(sys::StateSpace, Ad::Matrix, Cd::Matrix)
```

CCSのpp. 144を参照

# 引数:

  * `sys`: 拡張するシステム
  * `Ad`: 外乱の動力学
  * `Cd`: 外乱状態が`sys`の状態にどのように影響するか。この行列の形状は(sys.nx, size(Ad, 1))です。

[`add_low_frequency_disturbance`](@ref)や[`add_resonant_disturbance`](@ref)も参照してください。
