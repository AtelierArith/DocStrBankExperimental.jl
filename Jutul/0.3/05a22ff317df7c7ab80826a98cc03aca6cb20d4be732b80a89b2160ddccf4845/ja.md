```
get_diagonal_entries(eq::JutulEquation, eq_s)
```

キャッシュの対角エントリを取得します。つまり、エンティティタイプとインデックスが支配方程式のそれと等しいエントリです。

注意: この配列への変更には非常に注意してください。これは内部ADバッファへのビューであり、一貫性のないヤコビアンを作成するのは非常に簡単です。
