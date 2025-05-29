x,flag,err,iter,resvec = bicgstb(A,b,tol=1e-6,maxIter=100,M1=1.0,M2=1.0,x=[],out=0)

線形システム Ax=b に適用される双共役勾配安定化法。

入力:

A       - A*x を計算   b       - 右辺ベクトル   tol     - 誤差許容値   maxIter - 最大反復回数   M1,M2   - 前処理行列、または M1\x または M2\x を計算する関数   x       - 初期推定値   out     - 出力フラグ (-1: 出力なし, 0 : エラーのみ, 1 : 最終ステータス, 2: 各反復の相対残差)

出力:

x       - 解   flag    - 終了フラグ (  	0 : 望ましい許容値達成,   						-1 : 収束せずに maxIter に達した   						-2 : rho がゼロ   						-3 : norm(s)/bnrm2 < tol    						-4 : omega < 1e-16   						-9 : 右辺がゼロ)   err     - 誤差、すなわち norm(A*x-b)/norm(b)   iter    - 反復回数   resvec  - 各反復の誤差
