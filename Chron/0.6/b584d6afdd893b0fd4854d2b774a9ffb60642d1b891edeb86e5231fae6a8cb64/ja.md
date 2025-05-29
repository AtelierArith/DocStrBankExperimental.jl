```julia
screen_outliers(smpl::ChronAgeData; agemin=0.0, agemax=Inf, maxgap=100, make_plots=true, discordancemin=0, discordancemax=100)
```

`smpl`という`ChronAgeData`構造体から外れ値をスクリーニングします（`smpl.Path`内の`screened`サブディレクトリに新しいデータファイルを作成）。以下の条件でサンプルを拒否します。

a) `agemax`よりも古いか、`agemin`よりも若い

b) ギャップが`maxgap/N`シグマ（例：ゼノクリスト）を超える古い側にある

`make_plots`が`true`の場合、スクリーニング結果を示すプロットが`smpl.Path/screened`に作成されます。

基礎データがU-Pb比の形式である場合、追加のスクリーニングのために`discordancemin`および`discordancemax`キーワード引数も使用できます。
