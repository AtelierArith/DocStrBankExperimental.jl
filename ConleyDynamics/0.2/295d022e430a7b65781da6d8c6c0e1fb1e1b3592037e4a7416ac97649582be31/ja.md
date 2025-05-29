```
extract_multivectors(lc::LefschetzComplex, mvf::Vector{Vector{Int}},
                     scells::Vector{Int})
```

提供されたセルの選択を含むすべての多重ベクトルを抽出します。

この関数は、入力ベクトル `scells` に含まれるセルのうち少なくとも1つを含むすべての多重ベクトルを返します。返される引数の型は `Vector{Vector{Int}}` です。
