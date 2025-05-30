```
selective_eval!([interp::Interpreter=RecursiveInterpreter()], frame::Frame, isrequired::AbstractVector{Bool}, istoplevel=false)
```

`frame`内のコードを`JuliaInterpreter.finish_and_return!`の方法で実行しますが、`isrequired`で`false`とマークされたすべてのステートメントはスキップします。[`lines_required`](@ref)を参照してください。エントリ時に、必要に応じて呼び出し元は`frame.pc`が正しいステートメントに設定されていることを確認する必要があります。通常は`findfirst(isrequired)`です。自動的にそれを実行するには、[`selective_eval_fromstart!`](@ref)を参照してください。

`isrequired`は`frame`自体にのみ関連し、その呼び出し先には関連しません。

これにより、`BreakpointRef`、最後に実行されたステートメントから得られた値（`frame.framedata.ssavlues`に保存されている場合）、または`nothing`が返されます。通常、変数バインディングへの代入は、JuliaInterpreterによってssaストアを生成しません。
