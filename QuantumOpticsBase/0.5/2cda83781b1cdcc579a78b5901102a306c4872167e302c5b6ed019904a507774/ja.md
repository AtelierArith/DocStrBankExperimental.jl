```
time_stretch(op::TimeDependentSum, Sfactor)
```

[`TimeDependentSum`](@ref) `op`を`Sfactor`の因子で時間的にストレッチ（「長く」する）し、時間の係数関数`f(t)`を`f(t/Sfactor)`にします。新しい[`TimeDependentSum`](@ref)を返します。
