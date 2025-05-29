```
gpfitbayes(..., niter::Int=5000, warmup::Int=2000)
```

GPパラメータの事後分布からサンプルを生成します。

提供されるデータは、閾値を超えた超過分でなければなりません。すなわち、閾値を超えたデータから閾値を引いたものです。

# 引数

  * `niter::Int = 5000`: MCMCの総反復回数
  * `warmup::Int = 2000`: ウォームアップ反復回数（バーンイン）。

# 実装

この関数は、[Hoffman and Gelman, 2014](http://jmlr.org/papers/v15/hoffman14a.html)で実装されたNo-U-Turn Sampler (NUTS)を使用して、[Mamba.jl](https://mambajl.readthedocs.io/en/latest/index.html)パッケージから事後分布のランダムサンプルを生成します。

現在、実装されているのは不適切な一様事前のみです。すなわち、

$$
f_{(β₂,β₃)}(β₂,β₃) ∝ 1,
$$

ここで

$$
ϕ = X₂ × β₂,
$$

$$
ξ = X₃ × β₃.
$$

定常状態の場合、この不適切な事前は、サンプルサイズが2より大きい場合に適切な事後をもたらします（[Northrop and Attalides, 2016](https://www.jstor.org/stable/24721296?seq=1)）。

共変量は、モデルの適合を助けるためにパラメータを推定する前に標準化されます。フィッティングされたモデルを返す前に、元のスケールに戻されます。

他のメソッドについては、[`gpfitbayes`](@ref)、[`gpfitpwm`](@ref)、[`gpfit`](@ref)、および[`ThresholdExceedance`](@ref)も参照してください。

# 参考文献

Hoffman M. D. and Gelman A. (2014). The No-U-Turn sampler: adaptively setting path lengths in Hamiltonian Monte Carlo. *Journal of Machine Learning Research*, 15:1593–1623.

Paul J. Northrop P. J. and Attalides N. (2016). Posterior propriety in Bayesian extreme value analyses using reference priors. *Statistica Sinica*, 26:721-743.
