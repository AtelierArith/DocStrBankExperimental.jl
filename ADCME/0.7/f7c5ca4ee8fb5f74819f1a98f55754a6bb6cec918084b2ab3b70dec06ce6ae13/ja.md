```
empirical_sinkhorn(x::Union{PyObject, Array{Float64}}, y::Union{PyObject, Array{Float64}};
    reg::Union{PyObject,Float64} = 1.0, iter::Int64 = 1000, tol::Float64 = 1e-9, method::String="sinkhorn", dist::Function=dist, returnall::Bool=false)
```

Sinkhornアルゴリズムを用いて経験的Sinkhorn距離を計算します。ここで、$x$と$y$は二つの分布からのサンプルです。

  * `reg` (デフォルト = 1.0): エントロピー正則化パラメータ
  * `tol` (デフォルト = 1e-9)、`iter` (デフォルト = 1000): Sinkhornアルゴリズムのための許容誤差と最大反復回数
  * `dist` (デフォルト = 2): 二つのサンプル間の距離関数としての整数または関数; `dist`が整数の場合、$L$-距離ノルムが使用されます。
  * `returnall`: trueの場合は(`TransportMatrix`, `Loss`)を返します; そうでない場合は、`Loss`のみが返されます。

実装は https://github.com/rflamary/POT から適応されています。  
