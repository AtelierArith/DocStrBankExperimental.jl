```julia
exportdataset(dataset, [elements], filepath, delim;
    	floatout::Bool=false,
    	findnumeric::Bool=false,
    	skipnan::Bool=true,
    	digits::Integer,
    	sigdigits::Integer
    	rows=:
)
```

辞書または名前付きタプルのベクトルを列として持つ2次元配列に変換します。`dataset`をエクスポートします（`Dict`または`NamedTuple`の形式で）、オプションでエクスポートする`elements`を指定し、`filepath`で指定された名前の区切り付きASCIIテキストファイルとして、区切り文字`delim`を使用します。

可能なキーワード引数には以下が含まれます：

```
	digits
	sigdigits
```

出力を丸める絶対または有効桁数を指定します。デフォルトは丸めなしです。

```
	skipnan
```

`NaN`を区切り付き出力ファイルの空のセルとして残します。ブール値；デフォルトは`true`です。

```
	floatout
```

すべての出力を浮動小数点数として表現するか、そうでなければ`NaN`とします。ブール値；デフォルトは`false`です。

```
	findnumeric
```

数値列のみをエクスポートします。ブール値；デフォルトは`false`です。

```
	rows
```

エクスポートするデータセットの行を指定します。デフォルトの`:`はすべての行をエクスポートします。
