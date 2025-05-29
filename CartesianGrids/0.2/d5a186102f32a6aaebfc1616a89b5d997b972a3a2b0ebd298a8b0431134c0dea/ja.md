```
plan_laplacian(dims::Tuple,[with_inverse=false],[fftw_flags=FFTW.ESTIMATE],
                      [factor=1.0],[dx=1.0],[dtype=Float64])
```

演算子を設定して、次元 `dims` の双対または原始ノードデータ上で離散ラプラシアンを評価します。オプションのキーワード `with_inverse` が `true` に設定されている場合、逆ラプラシアン（格子グリーン関数、LGF）も設定されます。これらは、それぞれ適切なサイズのデータに対して `*` および `\` 演算を使用して適用できます。オプションのパラメータ `factor` は、演算子の結果を乗算し、逆数を除算するために使用されるスカラーです。オプションのパラメータ `dx` は、LGFの均一な値を大きな距離での連続的なアナログの動作に合わせるために使用されます。デフォルトでは1.0に設定されています。作用するデータの型はデフォルトで浮動小数点ですが、ComplexF64にもできます。これはオプションのパラメータ `dtype` で指定されます。

最初の引数の代わりに、ドメインのサイズを指定するために `w::Nodes` を供給することもできます。

# 例

```jldoctest
julia> w = Nodes(Dual,(5,5));

julia> w[3,3] = 1.0;

julia> L = plan_laplacian(5,5;with_inverse=true)
Discrete Laplacian (and inverse) on a (nx = 5, ny = 5) grid acting on Float64 data with spacing 1.0

julia> s = L\w
Nodes{Dual,5,5,Float64} data
Printing in grid orientation (lower left is (1,1))
5×5 Array{Float64,2}:
 0.16707    0.129276     0.106037     0.129276    0.16707
 0.129276   0.0609665   -0.00734343   0.0609665   0.129276
 0.106037  -0.00734343  -0.257343    -0.00734343  0.106037
 0.129276   0.0609665   -0.00734343   0.0609665   0.129276
 0.16707    0.129276     0.106037     0.129276    0.16707

julia> L*s ≈ w
true
```
