スパース（半）非負Tucker分解

非負テンソル`tnsr`をオプションで非負の`core`テンソルとスパース非負因子行列`factors`に分解します。

  * `tnsr` 非負の`N`モードテンソルを分解する
  * `core_dims` コアテンソルのサイズ
  * `core_nonneg` trueの場合、出力コアテンソルは非負
  * `tol` `tnsr`のフロベニウスノルムに対する分解の目標誤差
  * `max_iter` 誤差が`tol`を超えた場合の最大反復回数
  * `max_time` 最大実行時間
  * `lambdas` 因子行列とコアテンソルのための非負スパース正則化係数の`N+1`ベクトル
  * `Lmin` 残差誤差の勾配のリプシッツ定数の下限
  * `rw` 外挿重みを制御
  * `bounds` コアテンソルと因子行列の要素に許可される最大絶対値の`N+1`ベクトル（正則化が無効な場合のみ有効）
  * `ini_decomp` 初期分解、`:hosvd`の場合は`hosvd()`を使用して開始分解を生成し、`nothing`の場合はランダムな分解を使用
  * `verbose` アルゴリズムの進行状況をより多く出力

返されるもの：

  * 追加のプロパティを持つ`Tucker`分解オブジェクト：

```
* `:converged` メソッド収束指標
* `:rel_residue` 残差誤差`l(Z,U)`のフロベニウスノルムに正則化ペナルティ（ある場合）を加えたもの
* `:niter` 反復回数
* `:nredo` 目的関数の増加を避けるために`core`と`factor`が再計算された回数
* `:iter_diag` 各反復の収束情報、`SPNNTuckerState`を参照
```

この関数は、次の最適化問題を解くために交互近接勾配法を使用します： deqn{min 0.5 |tnsr - Z times*1 U*1 ldots times*K U*K |*{F^2} +  sum*{n=1}^{K} lambda*n |U*n|*1 + lambda*{K+1} |Z|*1, ;text{where; Z geq 0, U*i geq 0.}  `core_nonneg`が`FALSE`の場合、コアテンソル`Z`は負の要素を持つことが許可され、eqn{z*{i,j}=max(0,z*{i,j}-lambda*{K+1}/L*{K+1}})ルールはeqn{z*{i,j}=sign(z*{i,j})max(0,|z*{i,j}|-lambda*{K+1}/L_{K+1})}に置き換えられます。このメソッドは、誤差の相対改善が3回連続して許容誤差`tol`を下回るか、相対誤差改善と相対誤差（`tnsr`ノルムに関して）が許容誤差を下回る場合に停止します。そうでなければ、最大反復回数または時間制限に達した場合に停止します。

この実装は、Yangyang XuとWotao Yinによるntds_fapg() MATLABコードに基づいています。

Y. Xu, "スパース非負Tucker分解のための交互近接勾配法", Math. Prog. Comp., 7, 39-70, 2015を参照してください。http://www.caam.rice.edu/~optimization/bcu/を参照してください。
