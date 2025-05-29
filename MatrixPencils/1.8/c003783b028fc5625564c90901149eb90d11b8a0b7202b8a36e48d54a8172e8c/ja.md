```
 regbalance!(A, E; maxiter = 100, tol = 1, pow2 = true) -> (Dl,Dr)
```

行列 `M := abs(A)+abs(E)` の1ノルムを減少させることによって、通常のペア `(A,E)` をバランスさせます。これは、行列 `M` に対して反復的に適用される対角類似変換 `Dl*(A-λE)*Dr` を含み、`Dl*M*Dr` の行と列のノルムをできるだけ近づけることを目的としています。[Sinkhorn–Knoppアルゴリズム](https://en.wikipedia.org/wiki/Sinkhorn%27s_theorem) が使用され、`M` を二重確率行列に減少させます。

得られた `Dl` と `Dr` は対角スケーリング行列です。キーワード引数 `pow2 = true` が指定されている場合、得られた最適な `Dl` と `Dr` の成分は、それぞれ最も近い整数の2の累乗に置き換えられます。`pow2 = false` の場合、最適な値 `Dl` と `Dr` が返されます。得られた `Dl*A*Dr` と `Dl*E*Dr` は、それぞれ `A` と `E` を上書きします。

キーワード引数 `tol = τ`（`τ ≤ 1`）は、停止基準に使用される許容誤差を指定します。反復プロセスは、増分スケーリングが単位行列に `tol` 近いときに停止します。

キーワード引数 `maxiter = k` は、バランスアルゴリズムで許可される最大反復回数 `k` を指定します。

*注:* この関数は、MATLAB関数 `rowcolsums.m` に基づいており、[1] の修正が加えられ、スケーリング操作が直接 `A` と `E` に適用されるようになっています。

[1] F.M.Dopico, M.C.Quintana and P. van Dooren,      "Diagonal scalings for the eigenstructure of arbitrary pencils", SIMAX, 43:1213-1237, 2022.
