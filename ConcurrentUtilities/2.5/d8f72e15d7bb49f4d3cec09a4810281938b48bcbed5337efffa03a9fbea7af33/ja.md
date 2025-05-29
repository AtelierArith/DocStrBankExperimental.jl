```
try_with_timeout(f, timeout, T=Any) -> T
```

新しいタスクで `f` を実行し、その結果を返します。もし `f` が `timeout` 秒以内に完了しない場合、`TimeoutException` をスローします。もし `f` が例外をスローした場合、それを再スローします。もし `f` が正常に完了した場合、その結果を返します。`f` は `f(x::TimedOut)` の形式である必要があり、ここで `x` は `TimedOut` オブジェクトです。これにより、呼び出し関数は `x[]` をチェックすることでタイムアウトが発生したかどうかを確認でき、もし `true` であればタイムアウトが発生し、関数は優雅にキャンセル/中止できます。3番目の引数 `T` はオプションで（デフォルトは `Any`）、`f` が返すべき期待される戻り値の型を渡すことができます。これにより、`try_with_timeout` を `f` と共に使用する際の非推論による動的ディスパッチを回避できます。

# 例

```julia
julia> try_with_timeout(_ -> 1, 1)
1

julia> try_with_timeout(_ -> sleep(3), 1)
ERROR: TimeoutException: try_with_timeout timed out after 1.0 seconds
Stacktrace:
 [1] try_with_timeout(::var"#1#2", ::Int64) at ./REPL[1]:1
 [2] top-level scope at REPL[2]:1

julia> try_with_timeout(_ -> error("hey"), 1)
ERROR: hey
Stacktrace:
 [1] error(::String) at ./error.jl:33
 [2] (::var"#1#2")(::TimedOut{Any}) at ./REPL[1]:1
 [3] try_with_timeout(::var"#1#2", ::Int64) at ./REPL[1]:1
 [4] top-level scope at REPL[3]:1

julia> try_with_timeout(_ -> 1, 1, Int)
1

# `TimedOut` を使用した例
julia> try_with_timeout(1) do timedout
    while !timedout[]
        # 時間がかかる可能性のある反復計算を行う
    end
end

julia> try_with_timeout(1) do timedout
    sleep(3)
    timedout[] && abort_gracefully()
end
```
