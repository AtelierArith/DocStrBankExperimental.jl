```
DataFrame(mtg::Node)
DataFrame(mtg::Node, key)
```

MTGをDataFrameに変換します。

# 引数

  * `mtg::Node`: MTGノード（通常はルートノード）。
  * `key`: 属性名。シンボルとして与えられた変数のリストを選択します（高速）、文字列、または配列（またはタプル）。

# 例

```julia
# パッケージからMTGをインポートする:
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))),"test","files","simple_plant.mtg")
mtg = read_mtg(file)

# 完全なDataFrame:
DataFrame(mtg)

# :Lengthのみを選択:
DataFrame(mtg, :Length)

# :Lengthと:Widthのみを選択:
DataFrame(mtg, [:Length, :Width])
```
