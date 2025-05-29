```
master_int(W0, tspan, Ham_0, Ham_I; 
	reltol=1.0e-12, abstol=1.0e-12, int_reltol=1.0e-8, int_abstol=0.0, 
	fout=nothing, alg=DelayDiffEq.MethodOfSteps(DelayDiffEq.Vern6()))
```

量子マスター方程式を統合する

$$
\frac{d}{d t} \rho^{(I)}(t) = - \frac{i}{\hbar} [ \hat{H}_I^{(I)}(t), \rho^{(I)}(t_0) ]  -\frac{1}{\hbar^2} \int_{t_0}^{t_1} \text{d} \tau \: [ \hat{H}_I^{(I)}(t), [ \hat{H}_I^{(I)}(\tau), \rho^{(I)}(\tau) ]]
$$

$$
H = H_S + H_B + H_I = H_0 + H_I, \quad \hbar = 1.
$$

# 引数

  * `W0`: 初期状態ベクトル（ブラまたはケット）または初期伝播子。
  * `tspan`: 出力を表示する時間点を指定するベクトル。
  * `Ham_0`: 演算子としての系とバスのハミルトニアン。
  * `Ham_I`: 演算子としての相互作用ハミルトニアン。
  * `reltol`: DiffEqCallbacksソルバーおよびその内部状態の相対許容誤差。
  * `abstol`: DiffEqCallbacksソルバーおよびその内部状態の絶対許容誤差。
  * `int_reltol`: QuadGKソルバーおよびその内部状態の相対許容誤差。
  * `int_abstol`: QuadGKソルバーおよびその内部状態の絶対許容誤差。
  * `fout=nothing`: 指定された場合、この関数 `fout(t, rho)` は出力を表示するたびに呼び出されます。注意：状態 `rho` は正規化されておらず、永続的ではありません！それはまだODEソルバーによって使用されているため、変更してはいけません。
  * `alg`: DiffEqCallbacksがQME方程式を解くためのアルゴリズム。
