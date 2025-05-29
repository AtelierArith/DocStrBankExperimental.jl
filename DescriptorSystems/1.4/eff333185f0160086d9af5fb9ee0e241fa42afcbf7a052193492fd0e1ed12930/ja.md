```
  gprescale(sys; withB = true, withC = true) -> (sysbal, D1, D2)
```

記述子システム `sys = (A-λE,B,C,D)` のバランスを取るために、行列の1ノルムを減少させます。

```
         S =  ( abs(A)+abs(E)  abs(B) )
              (    abs(C)        0    )
```

対角行列 `D1` と `D2` を使用して、次の行列の行と列をできるだけノルムが近くなるようにします。

```
              diag(D1,I)  * S * diag(D2,I)
```

バランシングは、次の特定の行列に対してオプションで実行できます：

```
    S = abs(A)+abs(E),             if withB = false and withC = false ,
    S = ( abs(A)+abs(E)  abs(B) ), if withC = false,    
    S = ( abs(A)+abs(E) ),         if withB = false .
        (   abs(C)     )
```

結果として得られる `D1` と `D2` の対角要素は、[1] のアルゴリズムの修正バージョンから決定された最適な対角スケーリングの結果として得られる最も近い整数の2の累乗です。標準システム `E = I` の場合、`D1 = inv(D2)` であり、`D2` は LAPACK ファミリーのスケーリングアプローチ `*GEBAL.f` に基づいて計算されます。

この関数は、[MatrixPencils](https://github.com/andreasvarga/MatrixPencils.jl) パッケージの `lsbalance!` 関数へのインターフェースに過ぎません。

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022. 
