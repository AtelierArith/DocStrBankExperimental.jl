```
nwstr(n::Node{I,N}; internal=false)
```

`n`に根ざした木のためのnewickツリー文字列を生成します。これを機能させるために、`N`（`n.data`の型）は`name()`および`distance()`メソッドを実装する必要があります。オプションで`support()`も実装できます。データ型に対して`support`が実装されていて、それがNaNでない場合、内部ノードのラベリングには`name`よりも優先されます。例えば、`NewickData`型を参照してください。
