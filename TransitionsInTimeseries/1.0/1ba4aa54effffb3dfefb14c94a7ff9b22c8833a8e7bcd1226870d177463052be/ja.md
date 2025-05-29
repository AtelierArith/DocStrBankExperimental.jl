```
LowfreqPowerSpectrum(; q_lofreq = 0.1)
```

[`PrecomputableFunction`](@ref)を返し、[`PrecomputedLowfreqPowerSpectrum`](@ref)を生成するために必要なすべてのフィールドを含みます。後者は[`precompute`](@ref)によって初期化できます：

```julia
lfps = precompute( LowfreqPowerSpectrum() )
```

キーワード引数：

  * `q_lofreq`: `0`と`1`の間の数値で、どの部分の周波数スペクトルが低いと見なされるかを特徴付けます。例えば、`q_lofreq = 0.1`は、最低の10%の周波数が低いものと見なされることを意味します。
