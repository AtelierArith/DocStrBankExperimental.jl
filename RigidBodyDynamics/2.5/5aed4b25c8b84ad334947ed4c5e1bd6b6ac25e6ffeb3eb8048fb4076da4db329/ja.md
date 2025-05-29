```julia
bias_acceleration(state, joint)
bias_acceleration(state, joint, safe)

```

与えられたジョイントに対するバイアス加速度を返します。すなわち、すべてのジョイント加速度がゼロのとき、`frame_before(joint)`に対する`frame_after(joint)`の空間加速度を、メカニズムのルートフレームで表現します。
