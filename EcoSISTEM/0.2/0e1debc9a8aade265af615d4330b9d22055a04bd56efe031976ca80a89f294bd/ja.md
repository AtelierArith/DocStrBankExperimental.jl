```
abundances(cache::CachedEcosystem, tm::Unitful.Time)
```

生態系 `cache` の特定の時点 `tm` における個体数を抽出するための関数です。その時点の個体数が生態系に存在しない場合、関数はディスク上で最後に保存されたバージョンを確認し、前方にシミュレーションします。
