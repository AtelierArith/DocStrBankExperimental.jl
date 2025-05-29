```
DIMESampler(lprobFunc::Function, init::Array, niter::Int; sigma::Float64=1e-5, gamma=nothing, aimh_prob::Float64=0.05, nsamples_proposal_dist=nothing, df_proposal_dist::Int=10, rho::Float64=.999, progress::Bool=true)
```

# 引数

  * `lprobFunc::Function`: サンプリングされる尤度関数。ベクトル化されていることが期待されます。
  * `init::Array`: 初期エンサンブル。チェーンの数と `lprobFunc` の次元を推測するために使用されます。チェーンの数の目安は :math:`nchain = 5*ndim` です。
  * `niter::Int`: 実行する反復の数。
  * `sigma::Float=1e-5`: 提案ベクトルを伸ばすために使用されるガウス分布の標準偏差。
  * `gamma::Float=nothing`: 提案ベクトルの平均伸長係数。デフォルトでは、`ter Braak (2006) <http://www.stat.columbia.edu/~gelman/stuff_for_blog/cajo.pdf>`_ によって推奨される $2.38 / \sqrt{2\,\mathrm{ndim}}$ です。
  * `aimh_prob::Float=0.1`: AIMH提案を引く確率。
  * `rho::Float=0.999`: AIMH提案の平均と共分散の減衰パラメータ。
  * `df_proposal_dist::Float=10`: AIMH提案に使用される多変量t分布の自由度。
