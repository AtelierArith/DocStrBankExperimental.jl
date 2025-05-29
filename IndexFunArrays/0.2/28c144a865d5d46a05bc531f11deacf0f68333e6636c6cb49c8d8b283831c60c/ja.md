```
phase_kz([T=Float64], size::NTuple{N, Int};
offset=CtrFT,
dims=ntuple(+, N),
scale=ScaFT,
weight=1,
accumulator=sum)
1のzステップのための伝播位相（2π因子なし）を計算します。
`k_max_rel`の相対サンプリングには、`xy_scale = 2 ./ (k_max_rel .* sz[1:2])`をスケール引数として供給する必要があります。
複素場のナイキストサンプリングを達成するため、すなわちエヴァルド円が配列の側面に接触するためには、`scale=2 ./ sz[1:2]`となります。
伝播方程式は
Δz .* sqrt.(1-kxy_rel^2)を伝播位相として使用します。したがって、Z伝播距離Δzは媒質中の波長の単位（`λ = n*λ₀`）で指定する必要があります。
位相は2πではなく1に正規化されているため、次のようにこの位相を使用する必要があります：`cispi.(2.*phase_kz(...))`。
他の引数については、rrのような類似のスケーラーIndexFunArray関数を参照してください。
```

See also: `propagator()`
