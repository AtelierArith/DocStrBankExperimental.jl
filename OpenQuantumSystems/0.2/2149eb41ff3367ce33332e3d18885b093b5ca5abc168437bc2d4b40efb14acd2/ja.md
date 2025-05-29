```
master(W0, tspan, Ham; 
	reltol=1.0e-12, abstol=1.0e-12, int_reltol=1.0e-8, int_abstol=0.0, 
	fout=nothing, alg=DelayDiffEq.MethodOfSteps(DelayDiffEq.Vern6()))
```

量子マスター方程式を統合する 

$$
\frac{d}{d t} \rho(t) = - \frac{i}{\hbar} [ \hat{H}, \rho(t_0) ]  -\frac{1}{\hbar^2} \int_{t_0}^{t_1} \text{d} \tau \: [ \hat{H}, [ \hat{H}, \rho(\tau) ]]  ,\quad \hbar = 1.
$$

# 引数

  * `W0`: 初期状態ベクトル（ブラまたはケット）または初期伝播子。
  * `tspan`: 出力を表示するための時間点を指定するベクトル。
  * `Ham`: ハミルトニアンを指定する任意の演算子。
  * `reltol`: DiffEqCallbacksソルバーおよびその内部状態の相対許容誤差。
  * `abstol`: DiffEqCallbacksソルバーおよびその内部状態の絶対許容誤差。
  * `int_reltol`: QuadGKソルバーおよびその内部状態の相対許容誤差。
  * `int_abstol`: QuadGKソルバーおよびその内部状態の絶対許容誤差。
  * `fout=nothing`: 指定された場合、この関数 `fout(t, rho)` は出力を表示するたびに呼び出されます。注意：状態 `rho` は正規化されておらず、永続的ではありません！それはまだodeソルバーによって使用されているため、変更してはいけません。
  * `alg`: DiffEqCallbacksがQME方程式を解くためのアルゴリズム。
