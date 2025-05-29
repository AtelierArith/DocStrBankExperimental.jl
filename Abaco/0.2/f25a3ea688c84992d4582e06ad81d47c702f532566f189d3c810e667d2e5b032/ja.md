```
get_values(abaco, ne::String, var::String)::Dict{Int,Float64}
```

`ne`ノードの`var`値の時間順に並べられたシーケンスを返します。

返される値の辞書は、降順の時間で並べられており、最も最近の値が最初に来ます。エントリの数は、agesの値と同じかそれ以下です。
