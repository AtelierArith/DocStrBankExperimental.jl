x,flag,err,iter,resvec = cg(A,b,tol=1e-2,maxIter=100,x=[],storeInterm=false,out=0)

CGLS 共役勾配アルゴリズムが正規方程式に暗黙的に適用されます 

```
	(A'*A) x = A'*b.
```

入力:

A            - A*x = A(x,'F') および A'*x = A(x,'T') を計算する関数   b            - 右辺ベクトル   tol          - 誤差許容値、デフォルトは 1e-2   maxIter      - 最大反復回数、デフォルトは 100   x            - 初期推定値   storeInterm  - 中間解を返すためのフラグ（逆問題に役立つ）   out          - 出力のフラグ（-1: 出力なし、0 : エラーのみ、1 : 最終ステータス、2: 各反復のエラー）

出力:

x       - 近似解（interm==0）または近似解の履歴（interm==1）   flag    - 終了フラグ（  0 : 望ましい許容値が達成された、                         -1 : 収束せずに maxIter に達した                         -2 : 行列 A は正定値ではない                          -9 : 右辺がゼロだった）   eta     - 残差ノルム: norm(A*x-b)   rho     - 現在の反復のノルム: norm(x)
