```
AbstractMultiChannelColor{T<:Number,N}
```

マルチチャネル/マルチバンド/ハイパースペクトルカラーのための抽象型。具体的な派生型は、`channels`というフィールドを持つべきであり、これは`NTuple{N,T}`です。チャネルは`Tuple(c::AbstractMultiChannelColor)`で返すことができます。
