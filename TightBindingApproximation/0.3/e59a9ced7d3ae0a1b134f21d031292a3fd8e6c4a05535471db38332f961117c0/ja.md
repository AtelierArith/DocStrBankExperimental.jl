```
Fukui <: BerryCurvatureMethod
```

Fukui法はエネルギーバンドのベリー曲率を計算するためのものです。詳細は[Fukui et al, JPSJ 74, 1674 (2005)](https://journals.jps.jp/doi/10.1143/JPSJ.74.1674)を参照してください。ホール導電率（単一バンド）は次のように与えられます。

$$
\sigma_{xy} = -{e^2\over h}\sum_n c_n, \nonumber \\
c_n = {1\over 2\pi}\int_{BZ}{dk_x dk_y Ω_{xy}}, 
\Omega_{xy}=(\nabla\times {\bm A})_z,
A_{x}=i\langle u_n|\partial_x|u_n\rangle.
$$
