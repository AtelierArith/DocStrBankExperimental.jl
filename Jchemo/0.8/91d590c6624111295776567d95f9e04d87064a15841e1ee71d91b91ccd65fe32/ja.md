```
recod_catbyint(x; start = 1)
```

カテゴリ変数を整数に再コーディングします。

  * `x` : 置き換えるカテゴリ変数 (n)。
  * `start` : `x` の最初のカテゴリレベルを示す整数。

関数によって返される整数は、`x` のソートされたレベルに対応します。例を参照してください。

## 例

```julia
using Jchemo

x = ["b", "a", "b"]
mlev(x)   
[x recod_catbyint(x)]
recod_catbyint(x; start = 0)

recod_catbyint([25, 1, 25])
```
