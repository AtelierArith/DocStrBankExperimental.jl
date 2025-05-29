```
qs = gbalqual(sys; SysMat = false)
```

記述システム `sys = (A-λE,B,C)` の行列の1ノルムベースのスケーリング品質を計算します。

`SysMat = false` の場合、結果の `qs` は次のように計算されます。

```
    qs = max(qS(A),qS(E),qS(B),qS(C)) ,
```

ここで `qS(⋅)` は、非負行列のために定義されたスケーリング品質測定であり、ゼロ行またはゼロ列を持つ行列にも適用されるように拡張されています（定義5.5参照）。

`SysMat = true` の場合、結果の `qs` は次のように計算されます。

```
    qs = qS(S) ,
```

ここで `S` は次のように定義されるシステム行列です。

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

`qs` の大きな値は、状態空間モデルが適切にスケーリングされていない可能性を示します。標準システムで `E = I` の場合、上記の式は `E = 0` を仮定して使用されます。

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
