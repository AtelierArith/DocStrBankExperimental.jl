```julia
wμ, wσ, mswd = wmean(μ, σ; corrected=true, chauvenet=false)
wμ ± wσ, mswd = wmean(μ ± σ; corrected=true, chauvenet=false)
```

重み付き平均は、「地質年代学者のMSWD補正」を不確実性に適用するかどうかにかかわらず使用できます。平均値と標準偏差は、別々のベクトル `μ` と `σ` として指定することも、`Measurement`s の単一ベクトル `x` として指定することもできます。これは `x = μ .± σ` に相当します。

すべての場合において、`σ` は*実際の*シグマ（すなわち、1シグマ）として報告されると仮定されます。

`corrected=true` の場合、重み付き平均の結果の不確実性は、MSWD が `1` より大きい場合の分散を考慮するために `sqrt(mswd)` の因子で拡張されます。

`chauvenet=true` の場合、重み付き平均の計算の前に外れ値がチャーヴネの基準を使用して除去されます。

### 例

```julia
julia> x = randn(10)
10-element Vector{Float64}:
  0.4612989881720301
 -0.7255529837975242
 -0.18473979056481055
 -0.4176427262202118
 -0.21975911391551833
 -1.6250003193791873
 -1.6185557291787287
  0.25315988825847513
 -0.4979804844182867
  1.3565281078086726

julia> y = ones(10);

julia> wmean(x, y)
(-0.321824416323509, 0.31622776601683794, 0.8192171477885678)

julia> wmean(x .± y)
(-0.32 ± 0.32, 0.8192171477885678)

julia> wmean(x .± y./10)
(-0.322 ± 0.032, 81.9217147788568)

julia> wmean(x .± y./10, corrected=true)
(-0.32 ± 0.29, 81.9217147788568)
```
