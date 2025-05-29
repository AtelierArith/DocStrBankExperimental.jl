```
MINV = invsylvop(A, B; disc = false)
```

`MINV`を定義します。これは、`disc = false`の場合は連続シルベスター演算子 `M: X -> AX+XB` の逆であり、`disc = true`の場合は離散シルベスター演算子 `M: X -> AXB+X` の逆です。ここで、`A` と `B` は正方行列です。
