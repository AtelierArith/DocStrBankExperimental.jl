```
stripUnit(v)
```

`v`の単位を好ましい単位（デフォルトはSI単位）に変換し、その後単位を取り除きます。詳細については、[Unitful](https://painterqubits.github.io/Unitful.jl/stable/conversion/)の`upreferred`および`preferunits`を参照してください。

関数は次のように定義されています: `stripUnit(v) = ustrip.(upreferred.(v))`。
