```
readThermo(filename)
```

NASA 9次多項式熱力学定義ファイルを読み込みます。このファイルは、[NASA thermobuild](https://cearun.grc.nasa.gov/ThermoBuild/index_ds.html) から取得できます。戻り値は種の辞書です。

典型的なデータ形式については、[こちら](https://shepherd.caltech.edu/EDL/PublicResources/sdt/formats/nasa.html)を参照してください。

使用法: NASA 9次多項式定義ファイル `thermo.inp` が存在する場合、

`spec = readThermo("thermo.inp")`

は種の辞書を返します。

`readThermo` は2つの温度範囲（通常は200-1000 Kおよび1000-6000 K）のみを考慮しますが、必要に応じて追加することができます。
