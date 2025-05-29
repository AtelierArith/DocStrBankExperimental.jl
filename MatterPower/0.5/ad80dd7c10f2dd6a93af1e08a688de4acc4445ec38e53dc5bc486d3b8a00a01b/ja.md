```
dsigma2gausdR(pk, R)
```

ガウスフィルターの幅 `R` に関する質量揺らぎの分散の導関数、dσ^2/dR。

# 引数

  * `pk`(k): 引数 k が共動波数である線形物質パワースペクトルを返す関数。

      * **pk と k^3 の積は無次元でなければなりません**。例えば、k が h/Mpc の単位の場合、`pk` は Mpc^3/h^3 の単位でなければなりません。
  * `R::Real`: トップハットスムージングスケール。

      * **R と k の積は無次元でなければなりません**。例えば、k が h/Mpc の単位の場合、`R` は Mpc/h の単位でなければなりません。

`dsigma2gaus/dR` は次のように計算されます。

$$
dσ^2/dR = -2R ∫_0^∞ k^4dk exp(-k^2 R^2) pk(k) / (2π^2)
$$

この関数は [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/) に基づいています。
