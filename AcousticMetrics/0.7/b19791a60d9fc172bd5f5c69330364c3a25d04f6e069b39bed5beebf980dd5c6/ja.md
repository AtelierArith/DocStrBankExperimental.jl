```
AbstractNarrowbandSpectrum{IsEven,IsTonal,Tel} <: AbstractVector{Tel}
```

一般的な狭帯域音響メトリックのスーパークラスであり、要素型 `Tel` の不変の `AbstractVector` として機能します。

`IsEven` パラメータは、スペクトルの長さが偶数かどうかを示す `Bool` であり、ナイキスト周波数の計算に影響を与えます。`IsTonal` は、音響エネルギーが周波数帯域を通じてどのように分配されるかを示します：

  * `IsTonal == false` は、音響エネルギーが各帯域に均等に分配されると仮定されることを意味します
  * `IsTonal == true` は、音響エネルギーが各帯域の中心に集中していると仮定されることを意味します
