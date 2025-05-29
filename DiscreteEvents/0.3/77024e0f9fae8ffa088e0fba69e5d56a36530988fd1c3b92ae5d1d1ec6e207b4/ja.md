```
onthread(f::F, tid::Int; wait::Bool=true) where {F<:Function}
```

スレッド `tid` で関数 `f` を実行します。

1 以外のスレッドで `f` を実行すると、非同期タスクに依存している場合に大幅に速度が向上する可能性があります。

# 引数

  * `f::Function`:     実行する関数
  * `tid::Int`:        スレッド ID
  * `wait::Bool=true`: true の場合、関数の終了を待機します

# 例

```jldoctest
julia> using DiscreteEvents, .Threads

julia> onthread(2) do; threadid(); end
2
```
