```
warp(A::AbstractRaster, flags::Dict; kw...)
```

GDALの`gdalwarp`メソッドにアクセスするためのもので、`flag => value`引数の`Dict`を受け取ります。これらは文字列に変換可能で、複数のスペース区切りの引数が必要な場合はベクトルとしても指定できます。

GDALによって処理されない追加の次元を持つ配列（`X`、`Y`、`Band`以外）はスライスされ、ワープされ、元の配列の次元に合わせて結合されます。これらのスライスはこの段階ではディスクに書き込まれず、遅延ロードされます - 必要な場合は手動で行う必要があります。

引数のリストについては[the gdalwarp docs](https://gdal.org/programs/gdalwarp.html)を参照してください。

このメソッドを利用可能にするには`using ArchGDAL`を実行してください。

# キーワード

  * `missingval`: 欠損データを表す値で、通常はファイルから検出され、自動的に`missing`に変換されます。`0`や`NaN`などの代替値を設定することがパフォーマンス向上のために望ましい場合があります。`nothing`は欠損値がないことを指定します。同じ`missingval`を使用することで、置き換えのオーバーヘッドを削減できます。これは`missingval`関数を`missingval`として渡すことで実行できます。ファイルに不正な値がある場合、`correct_value => missing`や`correct_value => NaN`のようにペアで変換を手動で定義できます。`correct_value => correct_value`は変更のオーバーヘッドを削減します。注意: `raw=true`が設定されている場合、`missingval`はファイルに指定された値から変更されません。
  * `filename`: 直接書き込むためのファイル名で、大きなファイルに便利です。
  * `suffix`: ファイル名に追加する文字列または値。`suffix`のタプルはスタックレイヤーに適用されます。`keys(stack)`がデフォルトです。
  * `missingval`: ワープ中に使用する欠損値で、デフォルトは`Rasters.missingval(A)`になります。ペアを渡すことで、ワープ後に使用する欠損値を指定できます。

追加のキーワードは`ArchGDAL.Dataset`に渡されます。

## 例

これは単に`：tr`（出力ファイル解像度）と`：r`フラグを使用して配列を再サンプリングし、ピクセル化されたバージョンを提供します：

```jldoctest
using Rasters, ArchGDAL, RasterDataSources, Plots
A = Raster(WorldClim{Climate}, :prec; month=1)
a = plot(A)

flags = Dict(
    :tr => [2.0, 2.0],
    :r => :near,
)
b = plot(warp(A, flags))

savefig(a, "build/warp_example_before.png");
savefig(b, "build/warp_example_after.png"); nothing

# output

```

### `warp`の前：

![before warp](warp_example_before.png)

### `warp`の後：

![after warp](warp_example_after.png)

実際には、これには[`resample`](@ref)を好むべきです。しかし、`warp`はより柔軟かもしれません。

警告: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHubの問題を報告してください。
