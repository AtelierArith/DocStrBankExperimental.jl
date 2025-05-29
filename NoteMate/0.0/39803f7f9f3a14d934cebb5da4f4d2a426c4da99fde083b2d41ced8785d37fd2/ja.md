```
create_franklin_note(note::Note; date_format::String = "U d y")
```

汎用の `Note` を特別なメタデータを含む `[FranklinNote](@ref)` データ構造に変換します。

# 引数

  * `note`: 変換に使用される `Note` オブジェクト

# キーワード引数

  * `date_format`: 日付形式を受け入れる `String`；デフォルトは "U d y"（オプションについては `Dates.format` を参照）

# 戻り値

  * 新しく準備された `FranklinNote` オブジェクト

```
