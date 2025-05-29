x,flag,err,iter,resvec = ssor(A::SparseMatrixCSC, b::Vector; omega::Real=2/3, tol::Real=1e-2, maxIter::Int=1,out::Int=0)

線形システム A*x = b に適用される対称逐次過剰緩和。

!! メモリを節約するために上三角行列/下三角行列は決して構築されません !!

入力:

```
A       - スパース行列 CSC
b       - 右辺ベクトル
omega   - 緩和パラメータ (omega=1.0: ガウス・ザイデル)
tol     - 誤差許容値 (デフォルト=1e-2)
maxIter - 最大反復回数 (デフォルト=1)
out     - 出力フラグ (-1 : 出力なし, 0 : エラーのみ, 1 : 最終ステータス, 2: 各反復のエラー)
```

出力:

```
x       - 解
flag    - 終了フラグ (  0 : 望ましい許容値達成,
                      -1 : 収束せずにmaxIterに達した)
err     - 誤差、すなわち norm(A*x-b)/norm(b)
iter    - 反復回数
resvec  - 各反復の誤差
```
