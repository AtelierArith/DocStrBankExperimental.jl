```
@use "filename.dta", [clear]
```

ファイル `filename.dta` からデータを読み込み、グローバルデータフレームとして設定します。すでにグローバルデータフレームが存在する場合、`@use` は `clear` オプションが提供されない限りエラーをスローします。
