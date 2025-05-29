```
tgsyl!(A, B, C, D, E, F) -> (C, F, scale)
```

シルベスター行列方程式の系を解きます

```
  AX - YB = scale*C
  DX - YE = scale*F ,
```

ここで `X` と `Y` は未知の行列であり、ペア `(A, D)`、`(B, E)` および `(C, F)` は同じサイズを持ち、ペア `(A, D)` と `(B, E)` は一般化された（実数の）シュール標準形にあります。すなわち、`A`、`B` は上部準三角行列であり、`D`、`E` は上部三角行列です。`X`（`C` を上書き）と `Y`（`F` を上書き）、および `scale` を返します。

```
tgsyl!(trans, A, B, C, D, E, F) -> (C, F, scale)
```

`trans = 'T'` および実行列の場合、または `trans = 'C'` および複素行列の場合、（随伴）シルベスター行列方程式の系を解きます

```
  A'X + D'Y = scale*C
  XB' + YE' = scale*(-F) .
```

`tgsyl!('N', A, B, C, D, E, F)` は `tgsyl!(A, B, C, D, E, F)` の呼び出しに対応します。

LAPACK サブルーチン DTGSYL/STGSYL/ZTGSYL/CTGSYL へのインターフェース。
