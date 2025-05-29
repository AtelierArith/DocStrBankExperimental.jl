```
OnePhotonView(ψ::T) where {T<:SingleWaveguideKet}
```

ψは単一の波導のみを含み、波導インデックスは必要ありません。システムのインデックスは提供されず、基底状態が仮定されます。したがって、`OnePhotonView(ψ,index)`は`index = [1,:,1,...]`を返し、波導の位置には`:`があり、他のすべての位置には1があります。
