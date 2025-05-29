```
sixty(number) -> [deg, min, sec]
```

### 目的

小数を性分数に変換します。

### 説明

`ten` 関数の逆です。

### 引数

  * `number`: 性分数に変換される小数。

### 出力

`number` の性分数の対応物（度、分、秒）である三つの `AbstractFloat` の配列。

### 例

```jldoctest
julia> using AstroLib

julia> sixty(-0.615)
3-element StaticArraysCore.SVector{3, Float64} with indices SOneTo(3):
 -0.0
 36.0
 54.0
```

### 注意事項

この関数のコードは IDL Astronomy User's Library に基づいています。
