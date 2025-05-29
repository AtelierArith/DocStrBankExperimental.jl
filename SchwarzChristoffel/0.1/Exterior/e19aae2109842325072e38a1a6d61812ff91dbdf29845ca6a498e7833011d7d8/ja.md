```
PowerMap(c::Vector{ComplexF64}[;N = 200]) <: ConformalMap
```

単位円の外部から、冪級数係数 `c` によって定義された形状の外部への冪級数写像を作成します。

写像の形式は次の通りです。

$$
z(\zeta) = c_{1}\zeta + c_{0} + \sum_{j=1}^{N_{c}} \frac{c_{-j}}{\zeta^{j}}
$$

`c` のエントリは次のように対応します： `c[1]` $\rightarrow c_{1}$, `c[2]` $\rightarrow c_{0}$, `c[3]` $\rightarrow c_{-1}$, など。

結果として得られる写像 `m` は、単一またはベクトルの点 `ζ` で評価できます： `m(ζ)`。

# 例

```jldoctest
julia> c = ComplexF64[1,0,1/4];

julia> m = PowerMap(c)
Power series map

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.0+1.1im];

julia> m(ζ)
3-element Array{Complex{Float64},1}:
   1.025+2.925im
 -2.0625-1.9375im
     0.0+0.872727im
```
