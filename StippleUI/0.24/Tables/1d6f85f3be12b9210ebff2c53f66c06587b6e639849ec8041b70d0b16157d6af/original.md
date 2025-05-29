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

Create a cell template by passing `class` and `style` for styling and an `edit`-attribute for determining whether a cell can be edited. Furthermore the columns to be styled and/or edited can be specified via the `edit` and `columns` attributes. The attribute `type` determines the type of input and can be a vector, which is cycled when iterating the editable columns. A single cell template to a table can be defined by forwarding (almost) the same keywords to `table()`. The only slight modification is that the`keyowrds`style`and`class``type`are replaced by`cell*style`and`cell*class``cell_type` in order not to interfere with the tables class and style.

Two locations can be addressed by `class` and `style`

  * the full cell (td-element)
  * the inner element (div/input)

If a cell is editable, a reference table can be specified to monitor, whether a cell has been modified. For modified cells a separate set of class and style can be specified.

### Table of format specifiers

|                                          Name |                     Description |
| ---------------------------------------------:| -------------------------------:|
|                            `cell` and `style` |                  full cell (td) |
|               `inner_class` and `inner_style` |          inner cell (div/input) |
|             `change_class` and `change_style` |         modified full cell (td) |
| `change_inner_class` and `change_inner_style` | modified inner cell (div/input) |

Note that some formatting attributes cannot be changed by setting a class because some other css classes have higher precedence. Use the style attribute in such cases.

### Table of column specifiers

|                                                               edit |                                                            columns |                                            Description |
| ------------------------------------------------------------------:| ------------------------------------------------------------------:| ------------------------------------------------------:|
|                                                     `true`/`false` |                                                                  - |                                              all cells |
|                                                     `true`/`false` |   `"<column name>"` or `["<column name>", "<column name 2>", ...]` | specific columns, all of them editable or non-editable |
| `"<column name>"` or `["<column name 1>", "<column name 2>", ...]` |                                                                  - |                 specific columns, all of them editable |
| `"<column name>"` or `["<column name 1>", "<column name 2>", ...]` |                                                                 "" |     specific columns editable, all others non-editable |
| `"<edit column>"` or `["<edit column 1>", "<edit column 2>", ...]` | `"<column name>"` or `["<column name 1>", "<column name 2>", ...]` |             specific editable and non-editable columns |

### Example 1

All cells styled identically, column "name" editable, changing to indigo when a cell is modified

```julia

cell_template(edit = "name", ref_table = :ref_table, columns = "",
    cell_class = "text-blue-10 bg-blue-1",
    change_class = "text-indigo-10 bg-indigo-1"
)
```

### Example 2

Application of three templates to a table

```julia
df = DataFrame(name = ["Panda", "Lily"], email = ["panda@chihuahua.com", "lily@merckgroup.com"], age = ["", ""])

ui() = table(:table, cell_class = "text-blue-10 bg-blue-2",
    # column "name" blue but editable, with the inner cell highlighted and slightly padded, changing to indigo, if modified
    cell_template(edit = "email", ref_table = :ref_table,
        class = "text-blue-10 bg-blue-1", inner_class = "q-px-sm bg-blue-2",
        change_class = "bg-indigo-1", change_inner_class = "q-px-sm bg-indigo-2 text-indigo-10"
    ),
    # column "age" red (hint for entry to be filled), changing to green if filled)
    cell_template(edit = "age", type = "number", ref_table = :ref_table,
        class = "bg-red-1", inner_class = "q-px-sm bg-red-2",
        change_class = "bg-green-1", change_inner_class = "q-px-sm bg-green-2 text-green-8"
    )
)
```

Note that the general template for all cells is achieved via keyword forwarding from `table()`.

### Example 3

```julia
ui() = table(:table, edit = ["name", "email", "age"], cell_type = ["text", "text", "number"])
```
