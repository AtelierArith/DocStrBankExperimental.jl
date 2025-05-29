```
d2sigma2gausdR2(pk, R)
```

質量揺らぎの分散の二階導関数、d^2σ^2/dR^2、ガウスフィルターの幅 `R` に関して。

# 引数

  * `pk`(k): 引数 k がコモビング波数である線形物質パワースペクトルを返す関数。

      * **pk と k^3 の積は無次元でなければなりません**。例えば、k が h/Mpc の単位の場合、`pk` は Mpc^3/h^3 の単位でなければなりません。
  * `R::Real`: トップハットスムージングスケール。

      * **R と k の積は無次元でなければなりません**。例えば、k が h/Mpc の単位の場合、`R` は Mpc/h の単位でなければなりません。

`d2sigma2gaus/dR2` は次のように計算されます。

$$
d^2σ^2/dR^2 = -2 ∫_0^∞ (1 - 2x^2) k^4dk exp(-k^2 R^2) pk(k) / (2π^2)
$$

この関数は [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/) に基づいています。
