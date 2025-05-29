```
columns(itr, select::Selection = Cols())
```

行の反復可能なオブジェクトから、ベクトルのタプルとして1つ以上の列を選択します。

`select`は、どの列を選択するかを指定します。利用可能な選択オプションと構文については、[`select`](@ref)関数を参照してください。

`itr`は、`NDSparse`、`Columns`、`AbstractVector`、またはそれらの分散対応物である可能性があります。

# 例

```
t = table(1:2, 3:4; names = [:x, :y])

columns(t)
columns(t, :x)
columns(t, (:x,))
columns(t, (:y, :x => -))
```
