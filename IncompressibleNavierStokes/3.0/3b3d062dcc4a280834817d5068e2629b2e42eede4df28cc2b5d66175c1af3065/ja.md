```julia
processor(
    initialize
) -> NamedTuple{(:initialize, :finalize), <:Tuple{Any, IncompressibleNavierStokes.var"#283#284"}}
processor(
    initialize,
    finalize
) -> NamedTuple{(:initialize, :finalize), <:Tuple{Any, Any}}

```

時間ステッピングからの結果を処理します。時間ステッピングの前に、`initialize`関数が時間ステッパー`state`の可観測量に対して呼び出され、`initialized`を返します。可観測量は毎回の時間ステップで更新されます。

時間ステッピングの後、`finalize`関数が`initialized`と最終的な`state`に対して呼び出されます。

以下の例を参照してください：

```julia
function initialize(state)
    s = 0
    println("時間ステップを合計しましょう")
    on(state) do (; n, t)
        println("加算項は$n、時間は$tです")
        s = s + n
    end
    s
end

finalize(i, state) = println("最終合計（時間t=$(state.t)で）は$sです")
p = processor(initialize, finalize)
```

t=0からt=2までの6つの時間ステップで解決したとき、表示される出力は次のとおりです。

```
時間ステップを合計しましょう
加算項は0、時間は0.0です
加算項は1、時間は0.4です
加算項は2、時間は0.8です
加算項は3、時間は1.2です
加算項は4、時間は1.6です
加算項は5、時間は2.0です
最終合計（時間t=2.0で）は15です
```
