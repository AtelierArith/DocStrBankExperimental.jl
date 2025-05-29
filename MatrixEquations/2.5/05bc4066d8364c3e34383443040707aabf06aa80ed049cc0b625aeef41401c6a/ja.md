```
X = gsylvs!(A,B,C,D,E; adjAC=false, adjBD=false, CASchur = false, DBSchur = false)
```

一般化シルベスター行列方程式を解きます

```
            op1(A)Xop2(B) + op1(C)Xop2(D) = E,
```

ここで `A`、`B`、`C` および `D` は正方行列であり、

`op1(A) = A` および `op1(C) = C` もし `adjAC = false` の場合;

`op1(A) = A'` および `op1(C) = C'` もし `adjAC = true` の場合;

`op2(B) = B` および `op2(D) = D` もし `adjBD = false` の場合;

`op2(B) = B'` および `op2(D) = D'` もし `adjBD = true` の場合。

行列ペア `(A,C)` は一般化された実数または複素数シュール形式にあります。行列ペア `(B,D)` は `DBSchur = false` の場合に一般化された実数または複素数シュール形式にあり、または行列ペア `(D,B)` は `DBSchur = true` の場合に一般化された実数または複素数シュール形式にあります。ペンシル `A-λC` と `D+λB` は正則であり、共通の固有値を持ってはいけません。
