```
ODDict{K, V}
```

キーの型 `K` を値の型 `V` にマッピングする順序付き記述辞書です。さらに、各キー-値ペアの説明を文字列の形式で保存します。

値は順序付き辞書に保存されており、これはキー-値ペアの順序が保持されることを意味します。

値は `[]` 構文を使用してアクセスできます。例えば、`dict[key]` のように。説明は `()` 構文を使用してアクセスできます。例えば、`dict(key)` のように。値と説明は `[]` 構文を使用して設定できます。例えば、`dict[key] = value` または `dict[key] = (value, description)` のように、説明は `()` 構文を使用して設定できます。例えば、`dict(key, description)` のように。新しいキー-値ペアは常に辞書の末尾に追加されます。キーがすでに辞書に存在する場合、値と説明は更新されます。辞書の末尾にキー-値ペアを追加するには、新しいものであろうと古いものであろうと、`push!` または `merge` 関数を使用します。

### 例

```julia
julia> dict = ODDict("a" => 1, "b" => 2)
ODDict{String, Int64}
  a => 1 ()
  b => 2 ()

julia> dict["a"]
1

julia> dict["c"] = 3
3

julia> push!(dict, "d" => 4)
ODDict{String, Int64}
  a => 1 ()
  b => 2 ()
  c => 3 ()
  d => 4 ()

julia> dict["a"] = (5, "this is a")
(5, "this is a")

julia> dict
ODDict{String, Int64}
  a => 5 (this is a)
  b => 2 ()
  c => 3 ()
  d => 4 ()

julia> push!(dict, "a" => (5,"this is a"), "e" => (6,"this is e"))
ODDict{String, Int64}
  b => 2 ()
  c => 3 ()
  d => 4 ()
  a => 5 (this is a)
  e => 6 (this is e)
```
