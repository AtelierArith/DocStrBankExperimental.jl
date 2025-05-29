```
scale = studyscale(state;[verbose=false],[dbg=(;)])
```

モデルのスケーリングのための名前付きタプルの名前付きタプルを返し、`scaled.myclass.myfield`としてアクセスされます。例えば、`scale.X.tx1`のように。

!!! info
    現在、`scale`の形式は`setscale!`が期待する入力と同一ではありません：進行中の作業です。


`verbose=true`の場合、提案された`scale`の背後にある分析のレポートが出力されます。提案されたスケーリングは、入力として渡された`state`に依存します - 特定の増分行列に対して計算されます。

参照：[`setscale!`](@ref)
