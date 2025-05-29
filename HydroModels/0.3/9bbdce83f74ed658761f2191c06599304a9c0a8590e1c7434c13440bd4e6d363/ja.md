```
DirectInterpolation{D}(data::AbstractArray, ts::AbstractVector{<:Integer})
```

データ補間アルゴリズムではなく、直接インデックスを使用する同じインターフェースを提供する軽量補間タイプです。

# 引数

  * `data::AbstractArray`: 補間されるデータ配列
  * `ts::AbstractVector{<:Integer}`: データに対応する時間点

# インターフェース

DataInterpolations.jlの補間タイプと同じ呼び出し可能なインターフェースを実装しています：

  * `(interp::DirectInterpolation)(t)`: 時間`t`での値を取得

# 実装の詳細

補間計算を行うのではなく、このタイプは要求された時間インデックスの天井にあるデータ値を単純に返します。非整数の時間点`t`に対しては、`ceil(Int, t)`を使用して次の整数インデックスを取得します。

# 例

```julia
data = rand(100)
ts = 1:100
interp = DirectInterpolation(data, ts)
value = interp(1.7)  # data[2]（1.7の天井）を返す
```
