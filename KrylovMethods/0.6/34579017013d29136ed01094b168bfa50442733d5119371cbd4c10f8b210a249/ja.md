x,flag,err,iter,resvec = lsqr(A,b,;x=[],maxIter=20,atol=1e-10,btol=1e-10,condlim=1e6,out=1,doBidiag=false,                               storeInterm::Bool=false)

最小二乗QR法 (LSQR) を用いて解く

min_x || A x - b ||,

ここで A は過剰決定または不足決定であると仮定されます。

実装は以下の通りで、コメントは次の文献のアルゴリズムLSQRに言及しています：

Paige, C. C., & Saunders, M. A. (1982).  LSQR: An Algorithm for Sparse Linear Equations and Sparse Least Squares.  ACM Transactions on Mathematical Software (TOMS), 8(1), 43–71. doi:10.1145/355984.355989

必要な入力：

A       - (flag,v,alpha,x) の関数。              flag=='F' の場合                   x <- A*v + alpha*x (xを上書き)             elseif flag=='T'                  x <- A'*v + alpha*x (xを上書き)             end   b       - 右辺ベクトル

オプションの入力：

x           - 開始推定値 (オプション)   maxIter     - 最大反復回数   atol        - (推定された) 残差ノルムの誤差許容値 (適合システム用)   btol        - (推定された) 勾配ノルムの誤差許容値 (不適合システム用)   condlim     - (推定された) 条件数に基づいて停止するための値   out         - 出力フラグ (-1: 出力なし, 0: エラーのみ, 1: 最終ステータス, 2: 各反復の残差ノルム)   doBidiag    - 最終反復でのAの二重対角化を返す   storeInterm - 中間反復を保存して返す

出力：

x       - 近似解  flag    - 終了フラグ ( 0 : atolまたはbtolに基づいて停止,                       -1 : 収束せずにmaxIterに達した                       -2 : 条件数が大きすぎた                       -9 : 右辺がゼロであった)  his     - 各反復のステータス  U,S,V   - 二重対角化 (doBidiag==trueの場合のみ構築)
