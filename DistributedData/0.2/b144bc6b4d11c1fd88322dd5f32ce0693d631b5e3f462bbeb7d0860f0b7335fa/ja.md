```
dmapreduce(dInfo1::Dinfo, dInfo2::Dinfo, map, fold)
```

複数の `Dinfo` を同時に処理する `dmapreduce` のバリアント。データは同じワーカーのセットに同じ順序で分散されている必要があります。
