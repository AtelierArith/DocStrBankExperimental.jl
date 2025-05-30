```
print_tree(tree; kw...)
print_tree(io::IO, tree; kw...)
print_tree(f::Function, io::IO, tree; kw...)
print_tree(f::Function, g::Function, io::IO, tree; kw...)
```

`tree`のテキスト表現を指定された`io`オブジェクトに出力します。

# 引数

  * `f::Function` - 使用する[`printnode`](@ref)のカスタム実装。シグネチャは`f(io::IO, node; kw...)`である必要があります。
  * `g::Function` - 使用する[`print_child_key`](@ref)のカスタム実装。シグネチャは`g(io::IO, key;)`です。
  * `io::IO` - 書き込むIOストリーム。
  * `tree` - 出力するツリー。
  * `maxdepth::Integer = 5` - この深さでサブツリーの出力を切り捨てます。
  * `indicate_truncation::Bool = true` - 切り捨てられたノードの下に垂直の省略記号を表示します。
  * `charset::TreeCharSet` - 枝を出力するために使用する[`TreeCharSet`](@ref)。
  * `printkeys::Union{Bool, Nothing}` - 子ノードのキーを出力するかどうか（`pairs(children(node))`を使用）。`nothing`の値は、ノードごとに[`printkeys_default`](@ref)を使用して動作を決定します。
  * `printnode_kw = (;)` - `f`に転送するキーワード引数。

# 例

```julia
julia> tree = [1:3, "foo", [[[4, 5], 6, 7], 8]];

julia> print_tree(tree)
Vector{Any}
├─ UnitRange{Int64}
│  ├─ 1
│  ├─ 2
│  └─ 3
├─ "foo"
└─ Vector{Any}
   ├─ Vector{Any}
   │  ├─ Vector{Int64}
   │  │  ├─ 4
   │  │  └─ 5
   │  ├─ 6
   │  └─ 7
   └─ 8

julia> print_tree(tree, maxdepth=2)
Vector{Any}
├─ UnitRange{Int64}
│  ├─ 1
│  ├─ 2
│  └─ 3
├─ "foo"
└─ Vector{Any}
   ├─ Vector{Any}
   │  ⋮
   │
   └─ 8

julia> print_tree(tree, charset=AbstractTrees.ASCII_CHARSET)
Vector{Any}
+-- UnitRange{Int64}
|   +-- 1
|   +-- 2
|   \-- 3
+-- "foo"
\-- Vector{Any}
    +-- Vector{Any}
    |   +-- Vector{Int64}
    |   |   +-- 4
    |   |   \-- 5
    |   +-- 6
    |   \-- 7
    \-- 8
```
