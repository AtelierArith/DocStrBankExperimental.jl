```
qs = pbalqual(M, N)
```

行列ペンシル `M-λN` の1ノルムベースのスケーリング品質を計算します。

得られた `qs` は次のように計算されます。

```
    qs = qS(abs(M)+abs(N)) ,
```

ここで `qS(⋅)` は、非負行列のための[1]の定義5.5で定義されたスケーリング品質測定です。この定義は、ゼロ行またはゼロ列を持つ行列にも適用できるように拡張されています。もし `N = I` の場合、`qs = qs(M)` が計算されます。

`qs` の大きな値は、スケーリングが不十分な行列ペンシルの可能性を示します。

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
