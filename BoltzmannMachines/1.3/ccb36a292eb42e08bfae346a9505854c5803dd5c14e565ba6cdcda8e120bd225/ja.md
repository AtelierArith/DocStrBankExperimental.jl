```
computegradient!(optimizer, v, vmodel, h, hmodel, rbm)
```

RBM `rbm` の勾配を、サンプル `v` によって誘発された隠れ活性 `h` と、モデルからサンプリングして生成されたベクトル `vmodel` および `hmodel` を考慮して計算します。結果は `optimizer` に保存され、`updateparameters!` の呼び出しによって適用できるようになります。戻り値はありません。

RBM（PartitionedRBMを除く）にとって、これは同じタイプのRBMのフィールド `optimizer.gradient` に勾配を保存することを意味します。
