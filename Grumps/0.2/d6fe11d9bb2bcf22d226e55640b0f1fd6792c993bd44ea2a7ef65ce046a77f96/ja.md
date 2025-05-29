```
Estimator( s :: Symbol )
```

GrumpsEstimator型を作成して返します。

これは使用する推定器を指定する方法の1つです。しかし、内部で使用される正確なシンボルを渡す必要があるため、通常は*Estimator( s :: String )*メソッドの方が良い選択です。

可能な選択肢には以下が含まれます：

*:cler* 完全なCLER推定器  

*:cheap* 同じ限界分布を持つCLERの安価な代替品

*:mdle* MDLE、すなわち積のレベルモーメントなしのCLER

*:shareconstraint* シェア制約を持つ混合ロジット

*:mixedlogit* マイクロデータのみを使用した混合ロジット推定器

*:gmm* 同じモデルのGMM推定器（進行中：推奨されません）
