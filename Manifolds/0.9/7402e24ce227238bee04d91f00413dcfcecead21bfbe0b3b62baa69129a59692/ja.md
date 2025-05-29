```
rand(::ProbabilitySimplex; vector_at=nothing, σ::Real=1.0)
```

`vector_at`が`nothing`の場合、[`ProbabilitySimplex`](@ref)多様体`M`上の点`x`を、Fisher-Raoメトリックに関して一様（すなわち、正のオルタンが単体にマッピングされる`n`-球面に関して一様）なランダムに返します。これは、多変量ガウス分布からのサンプルのベクトル長を正規化することによって、`n`-球面への等距離埋め込みに従います。参照：[Marsaglia:1972](@cite)。

`vector_at`が`nothing`でない場合、標準偏差`σ`を持つ多変量ガウス分布をシフトさせて、ゼロの成分和を持つ（ガウス）ランダムベクトルを接空間$T_{p}\mathrm{\Delta}^n$から返します。
