```
Probabilities <: Array{<:AbstractFloat, N}
Probabilities(probs::Array [, outcomes [, dimlabels]]) → p
Probabilities(counts::Counts [, outcomes [, dimlabels]]) → p
```

`Probabilities`は、確率の`N`次元配列を格納し、配列の合計が1（正規化された確率質量）になることを保証します。ほとんどの場合、配列は標準ベクトルです。`p`自体は、格納された配列と同様に操作および反復することができます。

確率は、配列の軸を説明する`outcomes`に対応しています。もし`p isa Probabilities`であれば、`p.outcomes[i]`は`i`次元に沿った結果を含む抽象ベクトルです。結果は確率と同じ順序であるため、`p[i][j]`は結果`p.outcomes[i][j]`の確率です。配列の次元には名前が付けられており、`p.dimlabels`でアクセスできます。ここで、`p.dimlabels[i]`は`i`次元のラベルです。`outcomes`と`dimlabels`は、指定されていない場合は自動的に割り当てられます。入力が[`Counts`](@ref)のセットであり、`outcomes`と`dimlabels`が指定されていない場合、ラベルと結果はカウントから継承されます。

## 例

```julia
julia> probs = [0.2, 0.2, 0.2, 0.2]; Probabilities(probs) # will be normalized to sum to 1
 Probabilities{Float64,1} over 4 outcomes
 Outcome(1)  0.25
 Outcome(2)  0.25
 Outcome(3)  0.25
 Outcome(4)  0.25
```

```julia
julia> c = Counts([12, 16, 12], ["out1", "out2", "out3"]); Probabilities(c)
 Probabilities{Float64,1} over 3 outcomes
 "out1"  0.3
 "out2"  0.4
 "out3"  0.3
```
