x,flag,err,iter,resvec = minres(A,b,;x=[],maxIter=20,tol=1e-10,out=1)

最小残差法 (MINRES) は次の方程式を解くための手法です。

```
A x = b,
```

ここで、A は対称であり、かつ不定である可能性があります。

実装は次の文献の26ページに従っています。

Choi, S.-C. T. (2006).   Iterative Methods for Singular Linear Equations and Least-squares Problems.   Phd thesis, Stanford University.

また、次の文献も参照してください。

Paige, C. C., & Saunders, M. A. (1975).   Solution of sparse indefinite systems of linear equations.   SIAM Journal on Numerical Analysis.

必要な入力:

A       - 行列-ベクトル積を実行する関数、例: x -> A*x    b       - 右辺ベクトル

オプションの入力:

x        - 開始推測 (オプション)    maxIter  - 最大反復回数    btol     - ランチョスステップの誤差許容値    rtol     - 推定相対残差の誤差許容値    gtol     - 推定勾配ノルムの誤差許容値    condlim  - A の条件数推定の制限    out      - 出力フラグ (-1: 出力なし, 0: エラーのみ, 1: 最終ステータス, 2: 各反復の残差ノルム)

出力:

x       - 近似解   flag    - 終了フラグ (0: 収束, -1: maxIter, -2: ランチョス, -3: 条件)   relres  - 最終反復での推定相対残差   nrmG    - 最終反復での推定勾配ノルム   nrmA    - A の推定フロベニウスノルム   conA    - 条件数の推定   phi     - 各反復の relres
