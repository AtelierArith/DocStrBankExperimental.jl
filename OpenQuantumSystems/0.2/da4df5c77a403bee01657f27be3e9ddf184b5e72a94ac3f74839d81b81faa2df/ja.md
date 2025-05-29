```
schroedinger(psi0, tspan, H; 
	reltol=1.0e-12, abstol=1.0e-12, fout=nothing, alg=OrdinaryDiffEq.Tsit5())
```

シュレーディンガー方程式を統合して状態を進化させるか、伝播子を計算します。

$$
\frac{d}{d t}\vert\psi(t)\rangle = - \frac{i}{\hbar} \hat H\vert\psi(t)\rangle, \quad \hbar = 1
$$

。

# 引数

  * `psi0`: 初期状態ベクトル（ブラまたはケットのいずれか）または初期伝播子。
  * `tspan`: 出力を表示する時間のポイントを指定するベクトル。
  * `H`: ハミルトニアンを指定する任意の演算子。
  * `reltol`: OrdinaryDiffEqソルバーおよびその内部状態の相対許容誤差。
  * `abstol`: OrdinaryDiffEqソルバーおよびその内部状態の絶対許容誤差。
  * `fout=nothing`: 指定された場合、この関数 `fout(t, psi)` は出力を表示する必要があるたびに呼び出されます。注意: 状態 `psi` は正規化されておらず、永続的ではありません！それはまだodeソルバーによって使用されているため、変更してはいけません。
  * `alg`: OrdinaryDiffEqがシュレーディンガー方程式を解くためのアルゴリズム。
