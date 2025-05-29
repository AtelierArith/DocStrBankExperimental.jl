```
schedulable_fixed_priority(T)
```

[`AbstractRealTimeTaskSystem`](@ref) `T` が固定優先度スケジューラによってスケジュール可能かどうかを確認します。タスクはインデックスによって優先度が付けられます（低から高へ）。

# 例

期限が周期を超える場合の従来のTDAの使用に対するLehoczkyの反例：

```jldoctest lehoczky
julia> ts = TaskSystem([PeriodicTask(70, 70, 26), PeriodicTask(100, 118, 62)]);

julia> schedulable_fixed_priority(ts)
true
```

タスク2の期限を短縮すると、システムはスケジュール不可能になります：

```jldoctest lehoczky
julia> ts[2] = PeriodicTask(100, 116, 62);

julia> schedulable_fixed_priority(ts)
false
```
