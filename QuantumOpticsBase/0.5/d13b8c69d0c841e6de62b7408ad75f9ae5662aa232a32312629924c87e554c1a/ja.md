```
time_restrict(op::TimeDependentSum, t_from, t_to)
time_restrict(op::TimeDependentSum, t_to)
```

[`TimeDependentSum`](@ref) `op`を時間ウィンドウ`t_from <= t < t_to`に制限し、その範囲外の時間では正確にゼロになるようにします。`t_from`が指定されていない場合は、ゼロであると見なされます。新しい[`TimeDependentSum`](@ref)を返します。
