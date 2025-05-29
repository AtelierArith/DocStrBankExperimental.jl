```
GenericLevenshteinDistance(;icost, dcost, rcost)
```

レーベンシュタイン距離は、1つの文字列を別の文字列に変換するための最小の編集操作の数を測定します。挿入コスト `icost`、削除コスト `dcost`、および置換コスト `rcost` があります。スレッドセーフではないため、各スレッド用にコピーを使用してください。
