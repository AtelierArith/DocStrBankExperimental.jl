```
ThreadPools.readlog(io) -> Dict of (スレッド # => ジョブリスト)
```

[`LoggedThreadPool`](@ref) の出力を分析し、各スレッドの各ジョブの履歴を生成します。  

ジョブリスト内の各ジョブは次の構造体です：

```
struct Job
    id    :: Int
    tid   :: Int
    start :: Float64
    stop  :: Float64
end
```

各スレッド内のジョブのデフォルトのソート順は停止時間によります。 `io` は IO オブジェクトまたはファイル名のいずれかです。

# 例

```julia
julia> log = ThreadPools.readlog("mylog.txt")
Dict{Int64,Array{ThreadPools.Job,1}} with 3 entries:
  4 => ThreadPools.Job[Job(3, 4, 0.016, 0.327), Job(6, 4, 0.327, 0.928)]
  2 => ThreadPools.Job[Job(2, 2, 0.016, 0.233), Job(5, 2, 0.233, 0.749)]
  3 => ThreadPools.Job[Job(1, 3, 0.016, 0.139), Job(4, 3, 0.139, 0.546)]
```
