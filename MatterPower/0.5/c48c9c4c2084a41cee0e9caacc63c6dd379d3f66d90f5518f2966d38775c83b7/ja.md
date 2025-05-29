```
setup_halofit(pk)
```

この関数は、halofit非線形パワースペクトルの計算に必要な3つのパラメータ、[kσ, neff, C]を返します。

*参考文献*: Smith et al., MNRAS, 341, 1311 (2003) の付録C

# 引数

  * `pk`(k): 引数kがコモービング波数である線形物質パワースペクトルを返す関数。

      * **pk times k^3は次元を持たない必要があります**。例えば、kがh/Mpcの単位である場合、`pk`はMpc^3/h^3の単位でなければなりません。

この関数は[Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/)に基づいています。
