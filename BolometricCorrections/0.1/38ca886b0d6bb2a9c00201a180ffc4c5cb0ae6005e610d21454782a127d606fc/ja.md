```
chemistry(mix::AbstractBCTable)
chemistry(mix::AbstractBCGrid)
```

提供されたボロメトリック補正グリッドまたはテーブルに対して、`AbstractChemicalMixture`の正しい具体的インスタンスを返します。これは、この化学情報を取得するための便利なプログラム的手段を提供します。

```jldoctest
julia> grid = MISTBCGrid("JWST");

julia> chemistry(grid)
BolometricCorrections.MIST.MISTChemistry()

julia> table = grid(-1.5, 0.03);

julia> chemistry(table)
BolometricCorrections.MIST.MISTChemistry()
```
