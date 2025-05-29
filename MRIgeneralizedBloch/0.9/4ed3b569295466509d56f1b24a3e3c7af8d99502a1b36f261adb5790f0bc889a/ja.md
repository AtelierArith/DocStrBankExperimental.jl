```
interpolate_greens_function(f, κmin, κmax)
```

κminとκmaxの範囲でグリーン関数fを補間します。

補間には、チェビシェフ多項式を取り入れ、機械精度への近似を保証するApproxFun.jlパッケージを使用します。

# 例

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_superlorentzian((t-τ)/T2s)
0.1471246868094442

julia> Gint = interpolate_greens_function(greens_superlorentzian, 0, 20);


julia> Gint((t-τ)/T2s)
0.14712468680944407
```
