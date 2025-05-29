```
recenter(trans::Union{AbstractMatrix,Transformation}, origin::Union{AbstractVector, Tuple}) -> ctrans
```

新しい変換 `ctrans` を返します。ここで、点 `origin` は `trans` の座標の原点として機能します。`trans` を適用する前後に `±origin` による平行移動が行われるため、`trans` が線形である場合、次のようになります。

```
ctrans(origin) == origin
```

その結果、`recenter` は `trans` の出力空間が入力空間と同型である場合にのみ意味があります。

例えば、`trans` が回転行列である場合、`ctrans` は `origin` の周りに空間を回転させます。
