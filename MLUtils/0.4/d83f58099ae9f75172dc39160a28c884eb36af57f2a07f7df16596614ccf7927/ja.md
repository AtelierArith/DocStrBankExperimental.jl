```
shuffleobs([rng], data)
```

データセット `data` のすべての元の観測値をランダムに再配置したバージョンを返します。

`data` 自体の値はコピーされません。代わりにインデックスのみがシャッフルされます。この関数は [`obsview`](@ref) を呼び出してそれを実現します。つまり、返される値は `data` とは異なる型である可能性があります。

オプションとして、ランダム数生成器 `rng` を最初の引数として渡すことができます。

この関数が機能するためには、`data` の型が [`numobs`](@ref) と [`getobs`](@ref) を実装している必要があります。

他にも [`obsview`](@ref) を参照してください。

# 例

```julia
# 配列の場合、サブセットは SubArray 型になります
@assert typeof(shuffleobs(rand(4,10))) <: SubArray

# ランダムな順序で全ての観測値を反復処理
for x in eachobs(shuffleobs(X))
    ...
end
```
