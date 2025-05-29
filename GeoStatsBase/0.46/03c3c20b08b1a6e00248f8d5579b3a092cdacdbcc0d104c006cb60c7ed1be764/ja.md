```
describe(geotable)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; skipmissing=true)
```

`geotable`のすべての列の記述テーブルを返します。記述関数`fun₁`、`fun₂`、..., `funₙ`を使用し、`skipmissing`キーワード引数を使用して欠損値をスキップするかどうかを指定します。オプションで、ペアを渡すことで`funᵢ`に`nameᵢ`を定義できます。記述関数が渡されない場合、デフォルトの関数が使用されます。それらは次のとおりです：`mean`、`minimum`、`median`、`maximum`、`nmissing`。

```
describe(geotable; cols=[col₁, col₂, ..., colₙ])
describe(geotable; cols=(col₁, col₂, ..., colₙ))
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=[col₁, col₂, ..., colₙ], skipmissing=true)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=(col₁, col₂, ..., colₙ), skipmissing=true)
```

列`col₁`、`col₂`、..., `colₙ`の記述テーブルを返します。

```
describe(geotable; cols=regex)
describe(geotable; cols=regex)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=regex, skipmissing=true)
describe(geotable, fun₁, name₂ => fun₂, ..., funₙ; cols=regex, skipmissing=true)
```

`regex`に一致する列の記述テーブルを返します。

# 例

```julia
describe(geotable)
describe(geotable, mean, median)
describe(geotable, std, var, cols=(1, 3, 5))
describe(geotable, maximum, minimum, cols=[:a, :c, :e])
describe(geotable, :min => minimum, first, last, cols=("a", "c", "e"))
describe(geotable, :min => minimum, :max => maximum, cols=r"[ace]", skipmissing=false)
```
