```
lanv2(A, B, C, D) -> (RT1R, RT1I, RT2R, RT2I, CS, SN)
```

実数の2x2非対称行列 `[A,B;C,D]` のシュール分解を標準形式で計算します。出力時に `A`、`B`、`C`、`D` は標準化されたシュール形式の対応する要素で上書きされます。`RT1R+im*RT1I` と `RT2R+im*RT2I` は得られた固有値です。`CS` と `SN` は回転行列のパラメータです。LAPACK サブルーチン DLANV2/SLANV2 へのインターフェースです。
