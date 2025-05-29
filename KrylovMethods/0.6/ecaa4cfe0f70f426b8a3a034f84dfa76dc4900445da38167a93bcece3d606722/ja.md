x,flag,err,iter,resvec = fgmres(A,b,restrt,tol=1e-2,maxIter=100,M=1,x=[],out=0)

(flexible) Generalized Minimal residual ( (F)GMRES(m) ) メソッドが A*x = b に適用されます。

これは GMRES の「右前処理」バージョンです: A*M^{-1}Mx = b。左前処理については gmres.jl を参照してください。

入力:

A       - A*x を計算する関数 b       - 右辺ベクトル restrt  - 再起動間の反復回数 tol     - 誤差許容値 maxIter - 最大反復回数 M       - 前処理器、M\x を計算する関数 x       - 初期推定値 out     - 出力フラグ (0 : エラーのみ, 1 : 最終ステータス, 2: 各反復の誤差)

出力:

x       - 近似解 flag    - 終了フラグ (  0 : 望ましい許容値達成, 	-1 : 収束せずに maxIter に達した 	-9 : 右辺がゼロだった) 	err     - 相対残差のノルム、すなわち、ノルム(A*x-b)/ノルム(b) 	iter    - 反復回数 	resvec  - 各反復の相対残差のノルム

```
前処理器 M(r) はベクトルのコピーを返さなければなりません。r のメモリを再利用することはできません。
```
