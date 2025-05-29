```
str_c(strings::AbstractVector; sep::AbstractString="")
```

文字列のベクターを単一の文字列に結合します。

引数

  * `strings`: 入力文字列。
  * `sep`: 文字列の間の区切り文字。デフォルトは空の文字列です。
  * `collapse` : 提供された場合、指定された結合文字列で連結された文字列を結合します。提供されない場合、連結された文字列の配列を返します。

返り値 結合された文字列。

例

```jldoctest
julia> str_c(["apple", "banana", "pear", "pineapple"])
"applebananapearpineapple"

julia> str_c(["Michigan", "Maryland"] , ["MI", "MD"], sep = ", ")
2-element Vector{String}:
 "Michigan, MI"
 "Maryland, MD"

julia> str_c(["Michigan", "Maryland"] , ["MI", "MD"], sep = ", ", collapse =  ";   ")
"Michigan, MI;   Maryland, MD"
```
