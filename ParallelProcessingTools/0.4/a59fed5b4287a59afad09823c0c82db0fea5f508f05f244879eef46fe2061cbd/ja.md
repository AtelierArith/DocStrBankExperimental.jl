```
@wait_while [maxtime=nothing] [timeout_error=false] cond
```

`cond` が真である間待機し、`cond` を評価する間に徐々に増加するスリープ時間を使用します。

`cond` は任意のJulia式である可能性があります。

`maxtime` が実際の値で指定されている場合、`maxtime` 秒間のみ待機し、値がゼロまたは負の場合は全く待機しません。

`timeout_error` が `true` の場合、最大待機時間を超えた場合に `TimelimitExceeded` 例外をスローします。

例として、maxtimeを持つタスクを待機します：

```julia
task = Threads.@spawn sleep(10)
timer = Timer(2)
@wait_while !istaskdone(task) && isopen(timer)
istaskdone(task) == false
```
