```
@tlc [name]
```

この式がスレッドローカルカウンタを使用して評価される時間をカウントします。

# 例

```jldoctest
julia> using ThreadLocalCounters

julia> hello_world() = @tlc hello_world;
```
