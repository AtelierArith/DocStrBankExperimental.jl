```
shuffleobs(data, [obsdim], [rng])
```

すべての観測を含む `data` の「サブセット」を返しますが、観測の順序はシャッフルされています。

`data` 自体の値はコピーされません。代わりにインデックスのみがシャッフルされます。この関数は [`datasubset`](@ref) を呼び出してそれを実現しており、返される値は `data` とは異なる型である可能性があります。

```julia
# 配列の場合、サブセットは SubArray 型になります
@assert typeof(shuffleobs(rand(4,10))) <: SubArray

# ランダムな順序で全ての観測を反復処理
for (x) in eachobs(shuffleobs(X))
    ...
end
```

オプションの（キーワード）パラメータ `obsdim` を使用すると、どの次元が観測を示すかを指定できます。詳細については `LearnBase.ObsDim` を参照してください。

オプションの（キーワード）パラメータ `rng` を使用すると、シャッフルに使用される乱数生成器を指定できます。これは再現可能な結果が望ましい場合に便利です。デフォルトでは、グローバル RNG を使用します。詳細については、Julia の標準ライブラリの `Random` を参照してください。

この関数が機能するためには、`data` の型が [`nobs`](@ref) と [`getobs`](@ref) を実装している必要があります。詳細については [`DataSubset`](@ref) を参照してください。
