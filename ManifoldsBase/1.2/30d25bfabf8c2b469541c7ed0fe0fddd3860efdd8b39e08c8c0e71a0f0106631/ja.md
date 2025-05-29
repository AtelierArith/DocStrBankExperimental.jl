```
StabilizedRetraction <: AbstractRetractionMethod
```

再tractionは別の再tractionをラップし、数値的安定性のために結果の点を多様体に投影します。

# コンストラクタ

```
StabilizedRetraction(::AbstractRetractionMethod=ExponentialRetraction())
```
