```
recod_catbydict(x, dict)
```

カテゴリ変数を辞書レベルに再コーディングします。

  * `x` : 置き換えるカテゴリ変数 (n)。
  * `dict` : 古いレベルと新しいレベルの対応を示す辞書。

例を参照してください。

## 例

```julia
using Jchemo

dict = Dict("a" => 1000, "b" => 1, "c" => 2)
x = ["c" ; "c" ; "a" ; "a" ; "a"]
recod_catbydict(x, dict)

x = ["c" ; "c" ; "a" ; "a" ; "a" ; "e"]
recod_catbydict(x, dict)
```
