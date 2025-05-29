```
sylvds!(A,B,C; adjA = false, adjB = false)
```

離散シルベスター行列方程式を解きます

```
            op(A)Xop(B) + X =  C,
```

ここで `op(A) = A` または `op(A) = A'` は `adjA = false` または `adjA = true` の場合、それぞれ、`op(B) = B` または `op(B) = B'` は `adjB = false` または `adjB = true` の場合、それぞれです。`A` と `B` はシュール形式の正方行列であり、`A` と `-B` は共通の逆数固有値を持ってはいけません。`C` には出力として解 `X` が含まれます。
