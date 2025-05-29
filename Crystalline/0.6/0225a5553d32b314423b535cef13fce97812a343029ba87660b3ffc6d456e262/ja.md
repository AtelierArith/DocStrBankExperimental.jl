```
SymmetryVector(n::AbstractSymmetryVector) -> SymmetryVector
```

`n`の`SymmetryVector`実現を返します。`n`がすでに`SymmetryVector`である場合は、`n`を直接返します。通常、返される値は`n`の情報を直接参照します（すなわち、コピーではありません）。
