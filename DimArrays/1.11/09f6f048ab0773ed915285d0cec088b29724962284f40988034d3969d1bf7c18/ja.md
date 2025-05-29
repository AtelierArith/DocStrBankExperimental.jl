```
dictvector(vec, [:first, "second", ...]) = DimVector(vec, Dict(1 => :first, 2 => "second", ...))
dictvector(vec, [:first, ...], :axis, :content)
```

エントリにラベルを付ける辞書のインデックス関数を持つ（短い）`DimVector`を定義する便利な方法です。次元/軸の名前とその内容のラベルも指定できます。
