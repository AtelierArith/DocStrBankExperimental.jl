```
Interval(lb::Real, ub::Real)
```

一変数区間を表します。

フィールドは次のことを表します：

  * `lb`: 区間の下限
  * `ub`: 区間の上限

# 例

```jldoctest
julia> interval = Interval(0., 1.)
[0.00000, 1.00000]

julia> Interval()
ℝ

```
