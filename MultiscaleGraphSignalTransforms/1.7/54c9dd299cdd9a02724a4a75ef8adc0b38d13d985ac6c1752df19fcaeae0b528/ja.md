```
function rs_to_region(rs::Matrix{Any}, tag::Matrix{Any})
```

GPからのrs、tagの情報をもとに、dmatrix（展開係数行列）と同じサイズのtag_r行列を計算します。各要素は、展開ツリーにおける係数の位置を示します。

### 入力引数

  * `rs::Matrix{Any}`: GPからのrs、分割ツリーの情報を示します
  * `tag::Matrix{Any}`: GPからのtag、係数のタグを示します

### 出力引数

  * `tag_r::Matrix{UInt64}`: 分割ツリーの情報を示し、dmatrixと同じサイズです

```
