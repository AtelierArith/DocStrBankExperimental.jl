```
signal = Map(; kwargs...)::OrderedDict{Symbol,Any}
```

辞書の形式でキー/値ペアのセットを返します。Mapは、変数、パラメータ、または信号テーブルに一連の属性を関連付けるために使用されます。

次のキーが認識されます（すべて*オプション*です）：

| key     | value |
|:------- |:----- |
| `:info` | 短い説明。 |

さらに、任意の他の信号属性を希望するキーで`signal`に保存できます。

# 例

```julia
using SignalTables

sigTable = SignalTable(
   J = Par(value = 0.02),
   attributes = Map(author = "xyz")
)
```
