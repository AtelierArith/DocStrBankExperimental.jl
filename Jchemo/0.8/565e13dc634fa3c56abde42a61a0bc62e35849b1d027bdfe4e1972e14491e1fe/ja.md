```
recod_indbylev(x::Union{Int, Array{Int}}, lev::Array)
```

インデックス変数をレベルに再コーディングします。

  * `x` : 置き換えるインデックス変数 (n)。
  * `lev` : カテゴリーレベルを含むベクトル。

`slev = 'sort(unique(lev))'` と仮定すると、各要素 `x[i]` (i = 1, ..., n) は `slev[x[i]]` に置き換えられます。例を参照してください。

*警告*: ベクトル `x` は 1 から nlev までの整数を含む必要があります。ここで nlev は `lev` のレベルの数です。

## 例

```julia
using Jchemo

x = [2 ; 1 ; 2 ; 2]
lev = ["B" ; "C" ; "AA" ; "AA"]
mlev(x)
mlev(lev)
[x recod_indbylev(x, lev)]
recod_indbylev([2], lev)
recod_indbylev(2, lev)

x = [2 ; 1 ; 2]
lev = [3 ; 0 ; 0 ; -1]
mlev(x)
mlev(lev)
recod_indbylev(x, lev)
```
