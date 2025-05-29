```
発生
```

これは `AbstractOccurrence` のサブタイプで、以下のタイプがあります：

  * `what` - 種名、デフォルトは `""`
  * `presence` - 種の存在を示すブール値、デフォルトは `true`
  * `where` - WGS84での経度、緯度を示すタプル、または `missing`、デフォルトは `missing`
  * `when` - 観察の日付を示す `DateTime`、または `missing`、デフォルトは `missing`

インターフェースが `AbstractOccurrence` のサブタイプに対して適切に実装されると、*e.g.* `Occurrence(observation)` で直接 `Occurrence` オブジェクトを作成できます。同様に、自動的に実装された `convert` メソッドもあります。
