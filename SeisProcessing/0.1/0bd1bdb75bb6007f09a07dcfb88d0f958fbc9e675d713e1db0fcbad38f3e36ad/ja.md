```
Ricker(; <keyword arguments>)
```

Ricker ウェーブレットを作成します。

# 引数

  * `dt=0.002`: サンプリング間隔（秒）。
  * `f0=20.0`: 中心周波数（Hz）。

# 例

```julia
julia> w = Ricker(); plot(w);
julia> w = Ricker(dt=0.004, f0=20); plot(w);
```

# 参考文献

Sheriff, Robert, 2002, Encyclopedic Dictionary of Applied Geophysics, fourth ed.: Society of Exploration Geophysicists. Geophysical Reference Series No. 13.
