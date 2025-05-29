```
labelfreq!(dict, obj) -> Dict
```

は、与えられたラベル頻度マップ `dict` を `obj` 内の各ラベルの絶対頻度で更新します。

```
julia> ld = labelfreq([0, 1, 1, 0, 0])
Dict{Int64,Int64} with 2 entries:
  0 => 3
  1 => 2

julia> labelfreq!(ld, [1,0,0])
Dict{Int64,Int64} with 2 entries:
  0 => 5
  1 => 3
```
