```
ERA5Daily <: ERA5Custom
```

分析されるデータセットには時間ごとのデータが含まれていることを指定します。すべてのフィールドは `ERA5Dataset` のドキュメント文字列で指定されたものと同じです。ただし、フィールド `sldoi`、`pldoi` および `ptype` はすべて `N/A` に設定されています。なぜなら、`ERA5Daily` は気候データストアで利用できず、ダウンロードもできないからです。
