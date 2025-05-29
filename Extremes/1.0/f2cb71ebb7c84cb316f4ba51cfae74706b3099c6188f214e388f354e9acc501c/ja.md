```
gevfitbayes(..., niter::Int=5000, warmup::Int=2000)
```

GEVパラメータの事後分布からサンプルを生成します。

# 引数

  * `niter::Int = 5000`: MCMC反復の総数。
  * `warmup::Int = 2000`: ウォームアップ反復の数（バーンイン）。

# 実装

この関数は、[Hoffman and Gelman, 2014](http://jmlr.org/papers/v15/hoffman14a.html)で提案されたNo-U-Turnサンプラー（NUTS）を使用して、[Mamba.jl](https://mambajl.readthedocs.io/en/latest/index.html)パッケージで実装されている事後分布からランダムサンプルを生成します。

現在、実装されているのは不適切な一様事前のみであり、*すなわち*

$$
f_{(β₁,β₂,β₃)}(β₁,β₂,β₃) ∝ 1,
$$

ここで

$$
μ = X₁ × β₁,
$$

$$
ϕ = X₂ × β₂,
$$

$$
ξ = X₃ × β₃.
$$

定常状態の場合、この不適切な事前は、サンプルサイズが3より大きい場合に適切な事後をもたらします（[Northrop and Attalides, 2016](https://www.jstor.org/stable/24721296?seq=1)）。

共変量は、モデルの適合を助けるためにパラメータを推定する前に標準化されます。フィッティングされたモデルを返す前に、元のスケールに戻されます。

他のメソッドについては、[`gevfitbayes`](@ref)、[`gevfitpwm`](@ref)、[`gevfit`](@ref)、および[`BlockMaxima`](@ref)も参照してください。

# 参考文献

Hoffman M. D. and Gelman A. (2014). The No-U-Turn sampler: adaptively setting path lengths in Hamiltonian Monte Carlo. *Journal of Machine Learning Research*, 15:1593–1623.

Paul J. Northrop P. J. and Attalides N. (2016). Posterior propriety in Bayesian extreme value analyses using reference priors. *Statistica Sinica*, 26:721-743.
