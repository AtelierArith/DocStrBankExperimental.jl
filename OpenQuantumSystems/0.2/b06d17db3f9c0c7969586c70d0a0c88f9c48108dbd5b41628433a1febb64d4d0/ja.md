```
schroedinger_dynamic(psi0, tspan, f; 
	reltol=1.0e-12, abstol=1.0e-12, fout=nothing, alg=OrdinaryDiffEq.Tsit5())
```

時間依存シュレーディンガー方程式を統合して状態を進化させるか、または伝播子を計算します。

$$
\frac{d}{d t}\vert\psi(t)\rangle = - \frac{i}{\hbar} \hat H(t)\vert\rho(t)\rangle, \quad \hbar = 1
$$

。

# 引数

  * `psi0`: 初期状態ベクトル（ブラまたはケトのいずれか）または初期伝播子。
  * `tspan`: 出力を表示するための時間点を指定するベクトル。
  * `f`: 時間および状態依存のハミルトニアンを返す関数 `f(t, psi) -> H`。
  * `reltol`: OrdinaryDiffEqソルバーおよびその内部状態の相対許容誤差。
  * `abstol`: OrdinaryDiffEqソルバーおよびその内部状態の絶対許容誤差。
  * `fout=nothing`: 指定された場合、この関数 `fout(t, psi)` は出力を表示するたびに呼び出されます。注意: 状態 `psi` は正規化されておらず、永続的ではありません！それはまだodeソルバーによって使用されているため、変更してはいけません。
  * `alg`: OrdinaryDiffEqがシュレーディンガー方程式を解くために使用するアルゴリズム。
