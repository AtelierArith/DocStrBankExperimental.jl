```
analyze_dimer_fraction(smld::BasicSMLD)
```

フレームごとのダイマーの割合を計算します。

# 引数

  * `smld::BasicSMLD`: すべてのエミッターを含むSMLD

# 戻り値

  * `Tuple{Vector{Int}, Vector{Float64}}`: フレーム番号とダイマーの割合

# 例

```julia
# 時間にわたるダイマーの割合を計算
frames, fractions = analyze_dimer_fraction(smld)
plot(frames, fractions, xlabel="フレーム", ylabel="ダイマーの割合")
```
