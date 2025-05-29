```
word(string::AbstractString, start_index::Int=1, end_index::Int=start_index, sep::AbstractString=" ")
```

文字列から単語を抽出します。

引数

  * `string`: 入力文字列。
  * `start_index`: 単語の開始インデックス。デフォルトは1。
  * `end_index`: 単語の終了インデックス。デフォルトは`start_index`。
  * `sep`: 開始インデックスと終了インデックスの間の区切り文字。デフォルトはスペース。

返り値 抽出された単語が文字列から返されます。

例

```jldoctest
julia> word("Jane saw a cat", 1)
1-element Vector{SubString{String}}:
 "Jane"

julia> word("Jane saw a cat", 2)
1-element Vector{SubString{String}}:
 "saw"

julia> word("Jane saw a cat", -1)
1-element Vector{SubString{String}}:
 "cat"

julia> word("Jane saw a cat", 2, -1)
3-element Vector{SubString{String}}:
 "saw"
 "a"
 "cat"
```
