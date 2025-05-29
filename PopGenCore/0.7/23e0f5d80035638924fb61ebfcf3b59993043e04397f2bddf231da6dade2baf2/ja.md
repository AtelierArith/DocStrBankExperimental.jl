```
locationdata!(data::PopData; longitude::Vector{Float64}, latitude::Vector{Float64})
```

既存の `PopData` 地理座標データを置き換えます。**十進法の度数**を `AbstractFloat` の任意の `Vector` として受け取ります。

## 書式要件

  * 十進法の度数形式: `-11.431`
  * 方位の代わりに **必ず** 負の符号 `-` を使用すること
  * 位置データは `PopData` に表示されるサンプルの順序でなければなりません
  * 欠損データは `Missing` 型の `missing` 値としてコーディングする必要があります（`replace!()` を使用して実現できます）

### 例

```
ncats = @nancycats ;
x = rand(237) ; y = rand(237)
locationdata!(ncats, longitude = x, latitude = y)
```
