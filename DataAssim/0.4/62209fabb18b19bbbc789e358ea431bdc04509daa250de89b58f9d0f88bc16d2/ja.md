```
x,J = fourDVar(
        xi,Pi,ℳ,yo,R,H,nmax,no;
        innerloops = 10,
        outerloops = 2,
        tol = 1e-5)
```

モデル `ℳ` (`AbstractModel`) を用いた増分4D-Varで、初期条件 `xi` と誤差共分散 `Pi` から始まる `nmax` 時間ステップを指定された内外ループ数で実行します。観測 `yo`（ベクトルのベクトル）と誤差共分散 `R`（行列のベクトル）は、`no` で与えられた時間ステップで観測演算子 `H` (`AbstractModel`) を用いて同化されます。
