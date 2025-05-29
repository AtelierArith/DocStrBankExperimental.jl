GPSLCObjectのコンストラクタは、GPSLCObjectを構築する前に事後分布からサンプリングします。

```
GPSLCObject(hyperparams, priorparams, SigmaU, obj, X, T, Y)
GPSLCObject(hyperparams, priorparams, SigmaU, obj, nothing, T, Y)
GPSLCObject(hyperparams, priorparams, nothing, nothing, X, T, Y)
GPSLCObject(hyperparams, priorparams, nothing, nothing, nothing, T, Y)
```

完全モデルまたは観測された共変量のないモデル
