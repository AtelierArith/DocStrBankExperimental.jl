# GaussianMixtureAlignment.jl

GaussianMixtureAlignment.jlは、ガウス混合モデルを整列させるためのパッケージです。特に、[GOGMAアルゴリズム (Campbell, 2016)](https://arxiv.org/abs/1603.00150) の実装を使用して、各向同性（球状）ガウス分布の混合物のグローバル最適整列を見つけます。

# REPLヘルプ

?の後にアルゴリズムまたはコンストラクタ名を続けると、ヘルプがターミナルに表示されます。次を参照してください：

```
	?IsotropicGaussian 

	?IsotropicGMM 

	?IsotropicMultiGMM 

	?gogma_align 

	?tiv_gogma_align 

	?rocs_align
```
