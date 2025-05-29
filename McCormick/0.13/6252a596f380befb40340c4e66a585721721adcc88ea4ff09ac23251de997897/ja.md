```julia
abstract type RelaxTag
```

`abstract type` は、MCオブジェクトに適用される各オペレーターに対して実行される緩和の方法を定義するサブタイプを持ちます。現在、標準（Mitsos 2009）を使用することを指定する `struct NS` は完全にサポートされています。`struct Diff`（Khan 2017）および `struct MV`（Tsoukalas 2011）によって指定された微分可能なマコーミック緩和に対しては限定的なサポートが提供されています。標準のマコーミック緩和のラウンドセーフな実装は、進行中の作業である `struct NSSafe` によって指定されています。
