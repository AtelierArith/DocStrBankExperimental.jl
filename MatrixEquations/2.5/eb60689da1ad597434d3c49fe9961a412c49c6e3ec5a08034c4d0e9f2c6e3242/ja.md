```
M = sylvop(A, B; disc = false)
```

連続シルベスター演算子 `M: X -> AX+XB` を定義します。`disc = false` の場合、または離散シルベスター演算子 `M: X -> AXB+X` を定義します。`disc = true` の場合、ここで `A` と `B` は正方行列です。
