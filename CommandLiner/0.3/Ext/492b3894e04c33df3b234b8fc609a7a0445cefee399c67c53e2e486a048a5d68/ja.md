```
exty(path) ->  Symbol
```

パス拡張子を表すシンボルを返します：

```julia
julia> exty("myfile.jpg")
:jpeg

julia> exty("myfile.jpeg")
:jpeg
```

このシンボルは、`hasext`と共に使用して、拡張子グループ内のすべての拡張子をキャプチャするために使用できます。例えば、{"jpg", "jpeg", および "jpe"}。

`CommandLiner.Ext.show_extgroups()`を使用して拡張子グループを表示し、`CommandLiner.Ext.register_extgroups(::Vector{Vector{String}})`を使用してそれらを再定義できます。

特別なケースの空の拡張子を区別したい場合は`ext`を使用し、そうでない場合は`exty`を使用してください：

```julia
julia> (ext("myfile"), exty("myfile"))
(nothing, :_empty_)

julia> (ext("myfile."), exty("myfile."))
("", :_empty_)
```

欠損拡張子に使用されるシンボル（デフォルト：`:_empty_`）は、`CommandLiner.Ext.setsym_empty()`を介して上書きできます。
