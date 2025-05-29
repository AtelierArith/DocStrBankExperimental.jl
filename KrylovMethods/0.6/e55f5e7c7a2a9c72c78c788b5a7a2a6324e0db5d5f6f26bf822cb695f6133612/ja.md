x,flag,err,iter,resvec = blockBiCGSTB(A,b,tol=1e-6,maxIter=100,M1=identity,M2=identity,x=[],out=0)

複数の右辺を持つ線形システムAx=bに適用されるBi共役勾配安定化法のブロックバージョン。

論文に基づく: El Guennouni, A., K. Jbilou, and H. Sadok. "複数の右辺を持つ線形システムのためのBiCGSTABのブロックバージョン。"  Electronic Transactions on Numerical Analysis 16.129-142 (2003): 2. 

入力:

A       - A*xを計算   b       - 右辺ベクトル   tol     - 誤差許容値   maxIter - 最大反復回数   M1,M2   - 前処理行列、またはM1\xまたはM2\xを計算する関数 		  - M1とM2でメモリが再利用される場合、各々が戻りベクトルの独自のコピーを持つことを確認する   x       - 初期推定   out     - 出力フラグ (-1: 出力なし, 0 : エラーのみ, 1 : 最終ステータス, 2: 各反復でのrelres)

出力:

x       - 解   flag    - 終了フラグ (  	0 : 望ましい許容値が達成された,   						-1 : 収束せずにmaxIterに達した   						-2 : ||rho||_Fがゼロに等しい   						-3 : norm(s)/bnrm2 < tol    						-4 : omega < 1e-16   						-9 : 右辺がゼロだった)   err     - 誤差、すなわち、norm(A*x-b)/norm(b)   iter    - 反復回数   resvec  - 各反復での誤差
