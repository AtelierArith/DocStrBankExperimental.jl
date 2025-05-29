```
sigma2gaus(pk, R)
```

ガウスフィルター幅 `R` に対する質量変動の分散、σ^2(`R`)。

# 引数

  * `pk`(k): 引数 k がコモビング波数である線形物質パワースペクトルを返す関数。

      * **pk と k^3 の積は無次元でなければなりません**。例えば、k が h/Mpc の単位の場合、`pk` は Mpc^3/h^3 の単位でなければなりません。
  * `R::Real`: トップハットスムージングスケール。

      * **R と k の積は無次元でなければなりません**。例えば、k が h/Mpc の単位の場合、`R` は Mpc/h の単位でなければなりません。

`sigma2gaus(R)` は次のように計算されます。

$$
σ^2(R) = ∫_0^∞ k^2dk exp(-k^2 R^2) pk(k) / (2π^2)
$$

この関数は [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/) に基づいています。
