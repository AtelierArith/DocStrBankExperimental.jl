データフレームから変数を部分的に除外する

### 引数

  * `df`: テーブル
  * `formula::FormulaTerm`: `@formula`を使用して作成された式
  * `add_mean::Bool`: 返される変数に初期平均を追加すべきか？
  * `method::Symbol`: メソッドのためのシンボル。デフォルトは:cpu。代わりに、:gpuは`CuArrays`を必要とします。この場合、`double_precision = false`オプションを使用して`Float32`を使用します。
  * `maxiter::Integer`: 最大反復回数
  * `double_precision::Bool`: デミーニング操作はFloat64を使用すべきか？デフォルトはtrue。
  * `tol::Real`: 許容誤差
  * `align::Bool`: 欠損値がある場合、返されるデータフレームは元のデータフレームと整列すべきか？デフォルトはtrue。

### 戻り値

  * `::DataFrame`: 従属変数の数だけ列があり、元のデータフレームと同じ行数のデータフレーム。
  * `::Vector{Int}`: 各列の反復回数のベクトル
  * `::Vector{Bool}`: 各列の成功のベクトル

### 詳細

`partial_out`は、一連の変数を一連の回帰変数に回帰させた後の残差を返します。構文は`reg`に似ていますが、複数の従属変数を受け入れます。従属変数の数だけ列があり、元のデータフレームと同じ行数のデータフレームを返します。回帰モデルは、*いずれの*従属変数も欠損していない行のみに対して推定されます。最後に、`add_mean = true`オプションを使用すると、初期変数の平均が残差に追加されます。

### 例

```julia
using  RDatasets, DataFrames, FixedEffectModels, Gadfly
df = dataset("datasets", "iris")
result = partial_out(df, @formula(SepalWidth + SepalLength ~ fe(Species)), add_mean = true)
plot(layer(result[1], x="SepalWidth", y="SepalLength", Stat.binmean(n=10), Geom.point),
   layer(result[1], x="SepalWidth", y="SepalLength", Geom.smooth(method=:lm)))
```
