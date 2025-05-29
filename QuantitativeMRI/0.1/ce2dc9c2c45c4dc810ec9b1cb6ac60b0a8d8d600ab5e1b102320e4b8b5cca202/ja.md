```
mp2rage_comb(ima::Array{Complex{<:Real}})
mp2rage_comb(ima_magn::Array{<:Real},ima_phase::Array{<:Real})
```

2つの反転時間（TI）で取得した画像を組み合わせて、次の式を用いてMP2RAGE画像を作成します。imaは任意のサイズで構いませんが、最後の次元は2つのTIである必要があります。

もし振幅画像と位相画像が関数に渡されると、それらを組み合わせて複素画像を作成します。

$$
\text{MP2RAGE} = Re(\frac{ima_{TI_1} \times conj(ima_{TI_2})}{|ima_{TI_1}|^2+|ima_{TI_2}|^2})
$$

# 引数

  * `ima::Array{Complex{<:Real}}`: TI = 2の任意の次元の画像
  * `ima_magn::Array{<:Real},`: TI = 2の任意の次元の振幅画像
  * `ima_phase::Array{<:Real},`: TI = 2の任意の次元の位相画像

# キーワード

# 戻り値

  * MP2RAGE画像

# 参考文献

  * Marques JP, Kober T, Krueger G, van der Zwaag W, Van de Moortele P-F, Gruetter R. MP2RAGE, a self bias-field corrected sequence for improved segmentation and T1-mapping at high field. NeuroImage 2010;49:1271–1281 doi: 10.1016/j.neuroimage.2009.10.002.

```
