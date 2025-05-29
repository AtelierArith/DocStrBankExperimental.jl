```
function bosonize(oppair::Vector{Pair{String, Int}},
                  sites::Vector{Index{T}}) where T
```

与えられたオペレータ名の文字列と位置の形式 `Vector{Pair{String, Int}}` は、適切な場所にジョルダン-ウィグナー文字列 "F" を配置することでオペレータ文字列を「ボソナイズ」します。

#### 引数

  * `oppair::Vector{Pair{String, Int}}`: 位置を持つオペレータ名の入力文字列。
  * `sites::Vector{Index}`: ITensors の規約に従った全サイト `Index`。

#### 戻り値

  * `::Int`: 偶数 (+1) または奇数 (-1) の置換。
  * `::Vector{Pair{String, Int}}`: 修正されたオペレータ名と位置の文字列。
