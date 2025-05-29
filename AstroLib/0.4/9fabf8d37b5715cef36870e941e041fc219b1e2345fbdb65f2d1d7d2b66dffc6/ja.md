```
month_cnv(number[, shor=true, up=true, low=true]) -> month_name
month_cnv(name) -> number
```

### 目的

月の英語名とそれに対応する番号の間で変換します。

### 説明

例えば、「January」から1に、またはその逆に変換します。

### 引数

この関数には2つのメソッドがあり、1つは数値入力（および3つの可能なブールキーワード）で、もう1つは文字列入力です。

数値入力引数:

  * `number`: 月名に変換される月の番号。
  * `short`（オプションのブールキーワード）: trueの場合、月の略称（3文字）の名前が返されます。例: "Apr" または "Oct"。デフォルトはfalseです。
  * `up`（オプションのブールキーワード）: trueの場合、月の名前はすべて大文字になります。例: "APRIL" または "OCTOBER"。デフォルトはfalseです。
  * `low`（オプションのブールキーワード）: trueの場合、月の名前はすべて小文字になります。例: "april" または "october"。デフォルトはfalseです。

文字列入力引数:

  * `name`: 月番号に変換される月名。

### 出力

入力に応じて、月名または月番号が返されます。数値入力の場合、月名の形式はオプションのキーワードによって影響を受けます。

### 例

```jldoctest
julia> using AstroLib

julia> month_cnv.(["janua", "SEP", "aUgUsT"])
3-element Vector{Int64}:
 1
 9
 8

julia> month_cnv.([2, 12, 6], short=true, low=true)
3-element Vector{String}:
 "feb"
 "dec"
 "jun"
```
