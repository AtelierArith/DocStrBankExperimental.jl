```
ThreadPools.showstats([io, ]log)
```

提供されたログの統計分析を生成します。

# 例

```julia
julia> ThreadPools.showstats("mylog.txt")

    合計時間: 1.542 s
    ジョブの数: 8
    平均ジョブ時間: 0.462 s
    最小ジョブ時間: 0.111 s
    最大ジョブ時間: 0.82 s

    スレッド 2: 時間 1.542 s, ギャップ時間 0.0 s
    スレッド 3: 時間 1.23 s, ギャップ時間 0.0 s
    スレッド 4: 時間 0.925 s, ギャップ時間 0.0 s

```
