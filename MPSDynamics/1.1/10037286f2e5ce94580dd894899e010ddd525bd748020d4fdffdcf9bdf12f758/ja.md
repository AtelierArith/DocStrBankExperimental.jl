```
puredephasingmpo(ΔE, dchain, Nchain, chainparams; tree=false)
```

純粋脱相モデルのMPOを生成します。これはハミルトニアン $H = \frac{ΔE}{2} σ_z +  \frac{σ_z}{2} c_0 (b_0^\dagger + b_0) + \sum_{i=0}^{N-1} t_i (b_{i+1}^\dagger b_i +h.c.) + \sum_{i=0}^{N-1} ϵ_i b_i^\dagger b_i$ によって定義されます。

スピンはMPSのサイト1にあり、バスモードは右側にあります。

### 引数

  * `ΔE::Real`: スピンのエネルギー分裂
  * `dchain::Int`: チェーンサイトの物理次元の切り捨てられたヒルベルト空間
  * `Nchain::Int`: チェーン内のサイト数
  * `chainparams::Array{Real,1}`: バスチェーンのためのチェーンパラメータ。チェーンパラメータは標準形式で与えられます: `chainparams` $=[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$。
  * `tree::Bool`: trueの場合、`TreeNetwork`オブジェクトを返し、そうでない場合はMPOテンソルのベクトルを返します。
