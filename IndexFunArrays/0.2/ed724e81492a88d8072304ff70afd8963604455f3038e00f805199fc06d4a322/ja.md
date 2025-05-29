```
disc1([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit)
```

`rr2`を参照して、すべてのオプションの説明を確認してください。

中心までの半径が1.0以下のIndexFunArrayを返します。この関数は、`disc`関数の補助関数として主に使用されます。円の半径は`scale`パラメータによって調整できます。より便利なバージョンについては`disc`を参照してください。
