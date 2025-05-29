```
time_stretch(op::TimeDependentSum, Sfactor)
```

Stretch (in time) a [`TimeDependentSum`](@ref) `op` by a factor of `Sfactor` (making it 'longer'), so that the coefficient functions of time `f(t)` become `f(t/Sfactor)`. Return a new [`TimeDependentSum`](@ref).
