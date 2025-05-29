```
cell_template(;
    edit::Union{Bool, Integer, AbstractString, Vector{<:AbstractString}, Vector{<:Integer}} = false,
    columns::Union{Nothing, Bool, AbstractString, Vector{<:AbstractString}} = nothing,
    class::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,
    style::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,
    inner_class::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,
    inner_style::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,
    type::Union{Nothing,Symbol,AbstractString,Vector} = nothing,
    ref_table::Union{Nothing,Symbol} = nothing,
    ref_rows::Union{Nothing,Symbol} = nothing, # alternative way of referencing table data
    change_class::Union{Nothing,AbstractString,AbstractDict,Vector} = "text-red ",
    change_style::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,
    change_inner_class::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,
    change_inner_style::Union{Nothing,AbstractString,AbstractDict,Vector} = nothing,

    rowkey::String = ID,
    kwargs...)
```

`class`と`style`を渡してセルテンプレートを作成し、セルが編集可能かどうかを決定するための`edit`属性を指定します。さらに、スタイルを適用したり編集したりする列は、`edit`および`columns`属性を介して指定できます。属性`type`は入力のタイプを決定し、ベクターであることができ、編集可能な列を反復処理する際にサイクルします。テーブルに対して単一のセルテンプレートを定義するには、ほぼ同じキーワードを`table()`に転送します。唯一のわずかな修正は、`keywords`の`style`と`class`、`type`が、テーブルのクラスとスタイルに干渉しないように`cell*style`と`cell*class`、`cell_type`に置き換えられることです。

`class`と`style`で2つの場所にアクセスできます。

  * フルセル（td要素）
  * 内部要素（div/input）

セルが編集可能な場合、セルが変更されたかどうかを監視するために参照テーブルを指定できます。変更されたセルには、別のクラスとスタイルのセットを指定できます。

### フォーマット指定子の表

|                                        名前 |                    説明 |
| -----------------------------------------:| ---------------------:|
|                            `cell`と`style` |             フルセル (td) |
|               `inner_class`と`inner_style` |      内部セル (div/input) |
|             `change_class`と`change_style` |        変更されたフルセル (td) |
| `change_inner_class`と`change_inner_style` | 変更された内部セル (div/input) |

一部のフォーマット属性は、他のCSSクラスが優先されるため、クラスを設定することで変更できないことに注意してください。そのような場合は、スタイル属性を使用してください。

### 列指定子の表

|                                    edit |                              columns |                   説明 |
| ---------------------------------------:| ------------------------------------:| --------------------:|
|                          `true`/`false` |                                    - |               すべてのセル |
|                          `true`/`false` |  `"<列名>"`または`["<列名>", "<列名2>", ...]` | 特定の列、すべて編集可能または非編集可能 |
|    `"<列名>"`または`["<列名1>", "<列名2>", ...]` |                                    - |         特定の列、すべて編集可能 |
|    `"<列名>"`または`["<列名1>", "<列名2>", ...]` |                                   "" |    特定の列が編集可能、他は非編集可能 |
| `"<編集列>"`または`["<編集列1>", "<編集列2>", ...]` | `"<列名>"`または`["<列名1>", "<列名2>", ...]` |    特定の編集可能および非編集可能な列 |

### 例1

すべてのセルが同一のスタイルで、列「name」が編集可能で、セルが変更されるとインディゴに変わる

```julia

cell_template(edit = "name", ref_table = :ref_table, columns = "",
    cell_class = "text-blue-10 bg-blue-1",
    change_class = "text-indigo-10 bg-indigo-1"
)
```

### 例2

テーブルに3つのテンプレートを適用

```julia
df = DataFrame(name = ["Panda", "Lily"], email = ["panda@chihuahua.com", "lily@merckgroup.com"], age = ["", ""])

ui() = table(:table, cell_class = "text-blue-10 bg-blue-2",
    # 列「name」は青ですが編集可能で、内部セルがハイライトされ、わずかにパディングされ、変更されるとインディゴに変わります
    cell_template(edit = "email", ref_table = :ref_table,
        class = "text-blue-10 bg-blue-1", inner_class = "q-px-sm bg-blue-2",
        change_class = "bg-indigo-1", change_inner_class = "q-px-sm bg-indigo-2 text-indigo-10"
    ),
    # 列「age」は赤（入力が必要なヒント）、入力されると緑に変わります
    cell_template(edit = "age", type = "number", ref_table = :ref_table,
        class = "bg-red-1", inner_class = "q-px-sm bg-red-2",
        change_class = "bg-green-1", change_inner_class = "q-px-sm bg-green-2 text-green-8"
    )
)
```

すべてのセルに対する一般的なテンプレートは、`table()`からのキーワード転送によって達成されることに注意してください。

### 例3

```julia
ui() = table(:table, edit = ["name", "email", "age"], cell_type = ["text", "text", "number"])
```
