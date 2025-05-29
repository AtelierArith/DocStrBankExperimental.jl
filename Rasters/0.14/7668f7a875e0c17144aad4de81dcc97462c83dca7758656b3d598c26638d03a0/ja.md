```
classify!(x, pairs...; lower, upper, others)
classify!(x, pairs; lower, upper, others)
```

`x`の値を`pairs`の値に基づいてインプレースで分類します。

`Fix2`が使用されていない場合、`lower`および`upper`キーワード

`others`が設定されている場合、`pairs`でカバーされていない他の値はその値に設定されます。

# 引数

  * `x`: `Raster`または`RasterStack`
  * `pairs`: 各ペアは値と置き換えを含む、下限と上限の範囲のタプルおよび置き換え、または`Fix2`のタプルのような`(>(x), <(y)`です。

# キーワード

  * `lower`: `Fix2`が使用されていない場合、下限値に使用する比較（`<`または`<=`）。
  * `upper`: `Fix2`が使用されていない場合、上限値に使用する比較（`>`または`>=`）。
  * `others`: `pairs`に含まれていないすべての値に割り当てる値。`nothing`（デフォルト）を渡すと、それらは変更されません。

# 例

ディスクに`classify!`を実行する際の重要なステップ：

  * RasterDataSources.jlのバージョンを上書きしないように一時ファイルをコピーします。
  * `write=true`で`open`を使用して、ディスク書き込み権限でファイルを開きます。
  * すべての置き換え値と`other`に`Float32`のような`10.0f0`を使用します。ファイルは`Float32`として保存されるため、他の型を書き込もうとすると失敗します。

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots
# ファイルをダウンロードしてコピー
filename = getraster(WorldClim{Climate}, :tavg; month=6)
tempfile = tempname() * ".tif"
cp(filename, tempfile)
# クラスを定義
classes = (5, 15) => 10,
          (15, 25) => 20,
          (25, 35) => 30,
          >=(35) => 40
# 書き込み権限でファイルを開く
open(Raster(tempfile); write=true) do A
    classify!(A, classes; others=0)
end
# 変更をプロットするために再度開く
plot(Raster(tempfile); c=:magma)

savefig("build/classify_bang_example.png"); nothing

# 出力
```

![classify!](classify_bang_example.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
