```julia
bias_acceleration(state, body)
bias_acceleration(state, body, safe)

```

与えられた物体のバイアス加速度を世界に対して返します。すなわち、すべての関節加速度がゼロのとき、メカニズムのルートフレームに対して、`default_frame(body)`の空間加速度をルートフレームで表現します。
