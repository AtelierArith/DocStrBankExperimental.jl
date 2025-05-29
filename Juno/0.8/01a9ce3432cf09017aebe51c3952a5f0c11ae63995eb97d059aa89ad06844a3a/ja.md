```
@profiler exp [kwargs...]
```

現在収集されているプロファイルトレースをクリアし、提供された式をプロファイルして `Juno.profiler()` を介して表示します。

[`FlameGraphs.flamegraph`](@ref) が受け取ることができる任意のキーワード引数は、オプション引数 `kwargs...` として指定できます。

```julia
# 関数呼び出しをプロファイルする
@profiler fname(fargs)

# ccallsを含め、再帰呼び出しを圧縮する
@profiler fname(fargs) C = true recur = :flat
```
