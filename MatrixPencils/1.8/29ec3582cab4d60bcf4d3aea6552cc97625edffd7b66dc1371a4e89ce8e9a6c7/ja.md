```
 lsbalance!(A, E, B, C; withB = true, withC = true, pow2, maxiter = 100, tol = 1) -> (D1,D2)
```

行列の1ノルムを減少させます 

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

対応する記述子システムトリプル `(A-λE,B,C)` に対して、行と列のバランシングを行います。これは、`D1*(A-λE)*D2` という対角類似変換を `abs(A)+abs(E)` に反復的に適用して、次の行列の行と列が 

```
              diag(D1,I)  * S * diag(D2,I)
```

ノルムができるだけ近くなるようにします。

バランシングは、次の特定のシステム行列に対してオプションで実行できます:   

```
    S = abs(A)+abs(E), if withB = false and withC = false ,
    S = ( abs(A)+abs(E)  abs(B) ), if withC = false,     or    
    S = ( abs(A)+abs(E) ), if withB = false .
        (   abs(C)     )
```

キーワード引数 `maxiter = k` は、バランシングアルゴリズムで許可される最大反復回数 `k` を指定します。 

キーワード引数 `tol = τ` は、停止基準に使用される許容誤差を指定し、`τ ≤ 1` です。   

キーワード引数 `pow2 = true` が指定されている場合、結果の最適な `D1` と `D2` の成分は、最も近い整数の2の累乗に置き換えられ、この場合、行列のスケーリングは浮動小数点演算で正確に行われます。 `pow2 = false` の場合、最適な値 `D1` と `D2` が返されます。

*注:* この関数は、MATLAB関数 `rowcolsums.m` の拡張です [1]。 

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
