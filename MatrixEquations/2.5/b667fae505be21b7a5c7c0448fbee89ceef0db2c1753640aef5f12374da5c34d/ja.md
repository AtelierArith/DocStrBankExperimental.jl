```
sylvcs!(A,B,C; adjA = false, adjB = false)
```

連続シルベスター行列方程式を解きます

```
            op(A)X + Xop(B) =  C,
```

ここで `op(A) = A` または `op(A) = A'` は `adjA = false` または `adjA = true` の場合にそれぞれ対応し、`op(B) = B` または `op(B) = B'` は `adjB = false` または `adjB = true` の場合にそれぞれ対応します。`A` と `B` はシュール形式の正方行列であり、`A` と `-B` は共通の固有値を持ってはいけません。出力の `C` には解 `X` が含まれます。
