```
stripUnit(v)
```

`v`の単位を好ましい単位に変換し（デフォルトはSI単位）、その後単位を取り除きます。詳細については、[Unitful](https://painterqubits.github.io/Unitful.jl/stable/conversion/)の`upreferred`および`preferunits`を参照してください。

関数は次のように定義されています: `stripUnit(v) = ustrip.(upreferred.(v))`。
