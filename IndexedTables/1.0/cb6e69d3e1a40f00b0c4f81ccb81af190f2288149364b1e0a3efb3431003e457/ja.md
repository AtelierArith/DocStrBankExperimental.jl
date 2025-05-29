```
rows(itr, select = Cols())
```

行の反復可能なオブジェクトから、値のベクトルとして1つ以上のフィールドを選択します。選択オプションと構文については、[`select`](@ref) 関数を参照してください。

`itr` は [`NDSparse`](@ref)、`StructArrays.StructVector`、`AbstractVector`、またはそれらの分散対応物である可能性があります。

# 例

```
t = table([1,2],[3,4], names=[:x,:y])
rows(t)
rows(t, :x)
rows(t, (:x,))
rows(t, (:y, :x => -))
```
