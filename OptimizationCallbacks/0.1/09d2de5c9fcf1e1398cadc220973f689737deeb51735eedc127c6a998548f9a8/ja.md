```
EventTrigger(events)
```

指定されたイベントで[`trigger!`](@ref)関数を使用してトリガーします。

### 例

```jldoctest
julia> using OptimizationCallbacks

julia> callback = Callback(EventTrigger((:start, :end)), (_, value,_ ,_) -> @info( "現在の値: " * string(value)));

julia> begin
           @info "開始."
           OptimizationCallbacks.trigger!(callback, :start)
           callback(nothing, 10.)
           callback(nothing, 9.)
           callback(nothing, 7.)
           OptimizationCallbacks.trigger!(callback, :end)
           callback(nothing, 6.)
       end;
[ Info: 開始.
[ Info: 現在の値: 10.0
[ Info: 現在の値: 6.0
```
