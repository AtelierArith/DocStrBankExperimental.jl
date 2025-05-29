```
qs = lsbalqual(A, E, B, C; SysMat = false)
```

記述子システムトリプル `(A-λE,B,C)` の1ノルムベースのスケーリング品質を計算します。

`SysMat = false` の場合、結果の `qs` は次のように計算されます。

```
    qs = max(qS(A),qS(E),qS(B),qS(C)) ,
```

ここで `qS(⋅)` は、非負行列のための[1]の定義5.5で定義されたスケーリング品質測定です。この定義は、ゼロ行またはゼロ列を持つ行列もカバーするように拡張されています。

`SysMat = true` の場合、結果の `qs` は次のように計算されます。

```
    qs = qS(S) ,
```

ここで `S` は次のように定義されるシステム行列です。

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

`qs` の大きな値は、スケーリングが不十分な状態空間モデルの可能性を示します。

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022.  ```
