```
classify(x, pairs; lower=(>=), upper=(<), others=nothing)
classify(x, pairs...; lower, upper, others)
```

`x`の値を`pairs`の値によって分類した新しい配列を作成します。

`pairs`は、値のタプル`(2, 3)`、`Fix2`関数（例：`<=(1)`）、`Fix2`のタプル（例：`(>=(4), <(7))`）、またはIntervalSets.jlの区間（例：`3..9`や`OpenInterval(10, 12)`）を保持できます。`pairs`は、各行が下限、上限、置換を持つ`n * 3`の行列でも構いません。

タプルまたは`Matrix`が使用される場合、`lower`および`upper`キーワードは、下限および上限の境界がどのように選択されるかを定義します。

`others`が設定されている場合、`pairs`に含まれない他の値はその値に設定されます。

# 引数

  * `x`: `Raster`または`RasterStack`
  * `pairs`: 各ペアは値と置換を含む、下限と上限の範囲と置換のタプル、または`Fix2`のタプル（例：`>(x), <(y)`）です。

# キーワード

  * `lower`: 下限値に使用する比較（`<`または`<=`）を指定します。`Fix2`が使用されていない場合。
  * `upper`: 上限値に使用する比較（`>`または`>=`）を指定します。`Fix2`が使用されていない場合。
  * `others`: `pairs`に含まれないすべての値に割り当てる値。`nothing`（デフォルト）を渡すと、それらは変更されません。

# 例

```jldoctest
using Rasters, RasterDataSources, ArchGDAL, Plots
A = Raster(WorldClim{Climate}, :tavg; month=1)
classes = <=(15) => 10,
          15..25 => 20,
          25..35 => 30,
          >(35) => 40
classified = classify(A, classes; others=0, missingval=0)
plot(classified; c=:magma)

savefig("build/classify_example.png"); nothing

# output
```

![classify](classify_example.png)

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
