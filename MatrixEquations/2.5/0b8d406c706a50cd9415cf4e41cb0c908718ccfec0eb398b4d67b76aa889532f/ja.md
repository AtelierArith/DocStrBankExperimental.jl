```
 cgls(A, b; shift, abstol, reltol, maxiter, x0) -> (x, info)
```

`Ax = b` を解くか、`norm(Ax-b)` を最小化するために `CGLS` を使用します。これは非対称線形方程式および最小二乗問題のための共役勾配法です。 `A` は、矩形行列または `LinearMaps` パッケージで定義された線形演算子として指定できます。 `eltype(A) == eltype(b)` であることが望ましく、そうでない場合はエラーが発生するか、演算子-ベクトル積で追加の割り当てが発生する可能性があります。

キーワード引数 `shift` は正則化パラメータを指定します。 `shift = s` とします。 `s = 0`（デフォルト）の場合、`CGLS` は最小二乗問題のための共役勾配法の Hestenes と Stiefel の特化した形式です。 `s ≠ 0` の場合、システム `(A'*A + s*I)*b = A'*b` が解かれます。

絶対許容誤差 `abstol` と相対許容誤差 `reltol` を指定して反復プロセスを停止することができます（デフォルト: `abstol = 0`, `reltol = 1.e-6`）。

最大反復回数は `maxiter` を使用して指定できます（デフォルト: `maxiter = max(size(A),20)`）。

解の初期推定値はキーワード引数ベクトル `x0` を使用して指定できます（デフォルト: `x0 = missing`）。

結果として得られる名前付きタプル `info` には、収束に関連する情報が含まれています。内容は次の通りです：

```
 `info.flag`  - 収束フラグの値:  
                1, 収束が発生した場合; 
                2, 収束せずに最大反復回数に達した場合;
                3, 行列 `A'*A + s*I` が特異または不定のように見える場合;
                4, 不安定性が予想される場合、つまり `(A'*A + s*I)` が不定で `norm(x)` が減少した場合;  

 `info.resNE` - 正規方程式の相対残差 `norm(A'*b - (A'*A + s*I)*x)/norm(A'*b)`;  

 `info.iter`  - `x` が計算された反復回数。
```

この関数は、非対称線形方程式および最小二乗問題のための共役勾配法 `CGLS` の MATLAB 実装の翻訳です [`https://web.stanford.edu/group/SOL/software/cgls/`](https://web.stanford.edu/group/SOL/software/cgls/)。 コードの著者は Michael Saunders で、Per Christian Hansen、Folkert Bleichrodt、Christopher Fougner からの貢献があります。

*注:*  [`IterativeSolvers`](https://github.com/JuliaLinearAlgebra/IterativeSolvers.jl) パッケージで利用可能な2つの代替ソルバー `lsqr` と `lsmr` も使用できます。 たとえば、次の `lsqr` の呼び出しを代わりに使用できます：

```
  using IterativeSolvers
  lsqr(A, b; kwargs...) -> x[, history]
```

ここで `kwargs` にはソルバー固有のキーワード引数が含まれます。 `lsmr` に対しても同様の呼び出しが使用できます。    
