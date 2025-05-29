```
time_shift(op::TimeDependentSum, t0)
```

[`TimeDependentSum`](@ref) `op`を`t0`単位だけ時間的に前方にシフト（遅延）し、時間の係数関数`f(t)`を`f(t-t0)`にします。新しい[`TimeDependentSum`](@ref)を返します。
