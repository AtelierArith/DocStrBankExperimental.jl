```julia
resetVariableAllInitializations!(fgl)

```

`::AbstractDFG`内のすべての変数の初期化フラグをリセットします。

ノート

  * 数値はそのまま残りますが、初期化フラグが現在`false`であるため、推論が上書きされます。
