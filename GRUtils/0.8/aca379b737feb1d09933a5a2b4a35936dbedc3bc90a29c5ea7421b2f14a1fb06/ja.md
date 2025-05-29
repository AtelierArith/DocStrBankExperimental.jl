```
errorbar(x, y, err[, spec; kwargs...])
errorbar(x, y, errlow, errhigh[, spec; kwargs...])
```

エラーバーの系列を描画します。

エラーバーは、それぞれの `(x, y)` 点での `x` および `y` 座標とエラーバーのサイズによって定義されます。対称エラーバーの場合、ベクトル `err` のみが必要で、その合計サイズは `2 .* err` になります。非対称エラーバーの場合、2つのベクトル `errlow` と `errhigh` が必要で、エラーバーのサイズは `errlow .+ errhigh` になります。

オプションのフォーマット文字列 `spec` は、エラーバーの線のスタイルと色、および `(x, y)` でのマーカーを定義します。これは [matplotlib](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.plot.html) のように動作します。`specs` が指定されていない場合、エラーバーはマーカーなしで、事前定義された色のシーケンスで実線としてプロットされます。

さらに、エラーバーの外観を変更するために次のキーワード引数を使用できます：

  * `linewidth::Float64`: 線の幅のスケールファクター。
  * `markersize::Float64`: マーカーサイズのスケールファクター。
  * `linecolor`: 線の16進RGBカラーコード。
  * `horizontal::Bool`: 水平エラーバーを描画するには `true` に設定します。
  * `capwidth`: バーの「キャップ」の幅の固定値で、X軸の単位（または `horizontal` が `true` の場合はY軸の単位）で指定します。指定されていない場合、キャップの幅はデータポイント間の平均間隔の0.3倍に自動的に調整されます。

# 例

```julia
# サンプルデータを作成
x = LinRange(-2, 2, 10)
y = x.^3 .+ x.^2 .+ x .+ 6
err = LinRange(0.5, 3, 10)
# 対称の水平エラーバーを描画
errorbar(x, y, err, horizontal=true)
# マーカー付きの非対称エラーバーを描画
errorbar(x, y, err, err./2, "-o")

```
