```
recod_catbylev(x, lev)
```

カテゴリ変数をレベルに再コーディングします。

  * `x` : 置き換える変数 (n)。
  * `lev` : カテゴリレベルを含むベクトル。

`x` の i 番目にソートされたレベルは、`lev` の i 番目にソートされたレベルに置き換えられます。例を参照してください。

*警告*: `x` と `lev` は同じ数のレベルを含む必要があります。

## 例

```julia
using Jchemo

x = [10 ; 4 ; 3 ; 3 ; 4 ; 4]
lev = ["B" ; "C" ; "AA" ; "AA"]
mlev(x)
mlev(lev)
[x recod_catbylev(x, lev)]
xstr = string.(x)
[xstr recod_catbylev(xstr, lev)]

lev = [3; 0; 0; -1]
mlev(x)
mlev(lev)
[x recod_catbylev(x, lev)]
```
