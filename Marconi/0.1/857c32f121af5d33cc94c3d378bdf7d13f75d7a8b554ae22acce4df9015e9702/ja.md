```
cascade(net1,net2,net3,...,netN)
```

新しい `DataNetwork` を返します。これは net1, net2, net3,...netN のカスケード結果であり、`nets` は 2-Port `DataNetwork` オブジェクトと 2-Port `EquaionNetwork` オブジェクトの混合です。オプションで、結果のポイント数を指定するための kwarg `numpoints` を取ります。

方程式駆動ネットワークの取り扱いに関する詳細はドキュメントを参照してください。
