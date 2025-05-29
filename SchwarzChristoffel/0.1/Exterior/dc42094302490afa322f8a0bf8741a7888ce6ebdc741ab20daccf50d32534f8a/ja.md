```
ExteriorMap(p::Polygon[;tol::Float64][,ncoeff::Int]) <: ConformalMap
```

単位円の内部または外部から多角形 `p` の外部へのシュワルツ・クリストフェル写像を作成します。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p)
シュワルツ・クリストフェル写像: 単位円から4つの頂点を持つ多角形の外部への写像
```

`ExteriorMap(p;tol=1e-12)` は、許容誤差を `1e-12` に手動で設定します（デフォルトは `1e-8` です）。

`ExteriorMap(p;ncoeff=200)` は、写像の多重極展開の負のべきの係数の数を `200` に手動で設定します（デフォルトは `100` です）。

得られた写像 `m` は、単一またはベクトルの点 `ζ` で評価できます。`m(ζ[;inside::Bool])` の形式で使用します。点は単位円の外部にあると仮定されますが、オプション引数 `inside=true` を指定した場合は、円の内部にあると仮定されます。

# 例

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> ζ = [0.1,0.5-0.75im,-0.25-0.3im];

julia> m(ζ;inside=true)
3-element Array{Complex{Float64},1}:
   -6.9344-7.68965im
 0.0439774-1.11249im
   2.41181-0.044779im

julia> ζ = [1.0+3.0im,-2.0-2.0im,0.0+1.1im];

julia> m(ζ)
3-element Array{Complex{Float64},1}:
   0.81614+3.02956im
  -2.25237-2.08523im
 -0.333104+0.975837im
```
