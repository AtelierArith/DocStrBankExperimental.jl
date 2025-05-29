```
liouvilleVonNeumann(rho0, tspan, H; 
	reltol=1.0e-12, abstol=1.0e-12, fout=nothing, alg=OrdinaryDiffEq.Tsit5())
```

リウヴィル＝フォン・ノイマン方程式を統合して状態を進化させるか、伝播子を計算します。

$$
\frac{d}{d t} \rho(t) = - \frac{i}{\hbar} [ \hat H, \rho(t) ], \quad \hbar = 1
$$

。

# 引数

  * `rho0`: 初期状態ベクトル（ブラまたはケトである可能性があります）または初期伝播子。
  * `tspan`: 出力を表示するための時間点を指定するベクトル。
  * `H`: ハミルトニアンを指定する任意の演算子。
  * `reltol`: OrdinaryDiffEqソルバーおよびその内部状態の相対許容誤差。
  * `abstol`: OrdinaryDiffEqソルバーおよびその内部状態の絶対許容誤差。
  * `fout=nothing`: 指定された場合、この関数 `fout(t, rho)` は出力を表示する必要があるたびに呼び出されます。注意: 状態 `rho` は正規化されておらず、永続的ではありません！それはまだodeソルバーによって使用されているため、変更してはいけません。
  * `alg`: OrdinaryDiffEqがLvN方程式を解くために使用するアルゴリズム。
