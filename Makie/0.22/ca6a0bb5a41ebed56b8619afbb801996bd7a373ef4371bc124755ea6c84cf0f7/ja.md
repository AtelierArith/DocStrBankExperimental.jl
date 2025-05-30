```
series(curves)
```

カーブは次のようになります：

  * `AbstractVector{<: AbstractVector{<: Point2}}`：線のベクトルとしてのシリーズのネイティブ表現
  * `AbstractMatrix`：各行は線のy座標を表し、`x`は`1:size(curves, 1)`の範囲になります
  * `AbstractVector, AbstractMatrix`：上記と同じですが、最初の引数がすべての線のx値を設定します
  * `AbstractVector{<: Tuple{X<: AbstractVector, Y<: AbstractVector}}`：x座標とy座標のベクトルを含むタプルのベクトル

`marker`、`markersize`、`markercolor`、`strokecolor`、または`strokewidth`のいずれかが`!= nothing`に設定されている場合、散布図が追加されます。

## プロットタイプ

`series`関数のプロットタイプエイリアスは`Series`です。

## 属性

**`color`** =  `:lighttest`  — *ドキュメントは利用できません。*

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントは利用できません。*

**`labels`** =  `nothing`  — *ドキュメントは利用できません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントは利用できません。*

**`linestyle`** =  `:solid`  — *ドキュメントは利用できません。*

**`linewidth`** =  `2`  — *ドキュメントは利用できません。*

**`marker`** =  `nothing`  — *ドキュメントは利用できません。*

**`markercolor`** =  `automatic`  — *ドキュメントは利用できません。*

**`markersize`** =  `nothing`  — *ドキュメントは利用できません。*

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントは利用できません。*

**`solid_color`** =  `nothing`  — *ドキュメントは利用できません。*

**`space`** =  `:data`  — *ドキュメントは利用できません。*

**`strokecolor`** =  `nothing`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `nothing`  — *ドキュメントは利用できません。*
