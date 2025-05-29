```
halofit(pk, p, Ωmz, k)
```

この関数は、指定されたコモービング波数の値における非線形パワースペクトルの値を返します。

*参考文献*: Takahashi et al., ApJ, 761, 152 (2012) の付録

  * この参考文献は、Smith et al., MNRAS, 341, 1311 (2003) の付録Cで与えられたパラメータを更新します。
  * Takahashi et al. の式 (A6, A7) における (1+w) に比例する項は、この関数には含まれていません。

# 引数

  * `pk`(k): 引数 k がコモービング波数である線形物質パワースペクトルを返す関数。
  * `p::Array{T,1} where T <: Real`: `p = setup_halofit(pk)` から得られる三つの変数 [kσ, neff, C] を含む配列。
  * `Ωmz::Real`: 与えられた赤方偏移 z における物質密度パラメータ、例えば、$Ωmz = Ωm(1+z)^3 / [Ωm(1+z)^3 + Ωk(1+z)^2 + ΩΛ]$。
  * `k::Real`: コモービング波数。

      * **pk と k^3 の積は無次元でなければなりません**。例えば、`k` が h/Mpc の単位である場合、`pk` は Mpc^3/h^3 の単位でなければなりません。

この関数は [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/) に基づいています。
