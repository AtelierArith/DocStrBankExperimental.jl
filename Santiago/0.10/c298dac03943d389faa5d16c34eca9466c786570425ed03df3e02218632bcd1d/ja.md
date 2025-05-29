```julia
scale_massflows(
    sys::Santiago.System,
    n_users::Real
) -> Santiago.System

```

すべての質量流量の要約統計を `n_users` でスケーリングし、更新されたシステムの独立したコピーを返します。
