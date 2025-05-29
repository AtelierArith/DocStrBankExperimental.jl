```julia
function importdataset(filepath, [delim];
    	importas=:Dict,
    	elements=nothing,
    	standardize::Bool=true,
    	floattype=Float64,
    	skipstart::Integer=0,
    	skipnameless::Bool=true,
    	mindefinedcolumns::Integer=0
)
```

`filepath`で指定された区切りファイルを`delim`で区切って、`Dict`または`NamedTuple`の形式でデータセットとしてインポートします。

可能なキーワード引数には以下が含まれます：

```
	importas
```

インポートされたデータセットの形式を指定します。オプションには`:Dict`と`:Tuple`があります。

```
	elements
```

データセットの各要素（すなわち、列）に使用する名前を指定します。デフォルト値（`nothing`）は、`elements`がファイルの最初の行から読み取られることを意味します。

```
	standardize
```

可能な限り列を均一な型に変換します。ブール値；デフォルトは`true`です。

```
	floattype
```

数値データのための好ましい浮動小数点型。デフォルトは`Float64`です。

```
	skipstart
```

入力ファイルの先頭でこの数だけ行を無視します（入力ファイルにヘッダーや列名の前に他のテキストがある場合に便利です）。デフォルトは`0`です。

```
	skipnameless
```

列名がない列をスキップします。ブール値；デフォルトは`true`です。

```
	mindefinedcolumns
```

この数未満の区切り文字を持つ行をスキップします。デフォルトは`0`です。
