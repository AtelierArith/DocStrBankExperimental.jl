```
ret = debug_command(interp::Interpreter, frame::Frame, cmd::Symbol, rootistoplevel::Bool=false;
                    line::Union{Nothing,Integer}=nothing)
ret = debug_command(frame::Frame, cmd::Symbol, rootistoplevel::Bool=false; line=nothing)
```

1つの「デバッガー」コマンドを実行します。キーワード引数はすべてのデバッグコマンドで使用されるわけではありません。`cmd` は次のいずれかである必要があります：

  * `:n`: 次の行に進む
  * `:s`: 次の呼び出しにステップインする
  * `:sl`: 現在の行の最後の呼び出しにステップインする（例：行が `f(g(h(x)))` の場合、`f` にステップインします）。
  * `:sr`: 現在の関数が戻るまでステップする
  * `:until`: 指定された場合はフレームを行 `line` に進め、それ以外の場合は現在の行の次の行に進める
  * `:c`: 終了またはブレークポイントに達するまで実行を続ける
  * `:finish`: 現在のフレームを終了し、親に戻る

または「高度な」コマンドのいずれか

  * `:nc`: 次の呼び出しに向けて前進する
  * `:se`: 単一のステートメントを実行する
  * `:si`: 単一のステートメントを実行し、呼び出しの場合はステップインする
  * `:sg`: 生成された関数のジェネレーターにステップインする

`rootistoplevel` と `ret` は [`JuliaInterpreter.maybe_reset_frame!`](@ref) に記載されている通りです。
