```
dsigma2dR(pk, R)
```

質量揺らぎの分散の導関数、dσ^2/dR、を半径 `R` のトップハットフィルターに関して計算します。

# 引数

  * `pk`(k): 引数 k が共動波数である線形物質パワースペクトルを返す関数。

      * **pk と k^3 の積は無次元でなければなりません**。例えば、k の単位が h/Mpc の場合、`pk` の単位は Mpc^3/h^3 でなければなりません。
  * `R::Real`: トップハット平滑化スケール。

      * **R と k の積は無次元でなければなりません**。例えば、k の単位が h/Mpc の場合、`R` の単位は Mpc/h でなければなりません。

`dsigma2/dR` は次のように計算されます。

$$
dσ^2/dR = 2 ∫_0^∞ k^2dk W(kR) dW/dR pk(k) / (2π^2)
$$

ここで、W(kR) は次のように与えられるウィンドウ関数です。

$$
W(x) = (3/x)j_1(x) = (3/x)(sin(x)/x^2 - cos(x)/x)
$$

dW/dR はその導関数です：

$$
dW/dR = k dW/dx = (-3k/x)j_2(x) = (-3k/x)[(3/x^2-1)sin(x)/x - 3cos(x)/x^2]
$$

j_n(x) は n 次の球ベッセル関数です。

この関数は [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/) に基づいています。
