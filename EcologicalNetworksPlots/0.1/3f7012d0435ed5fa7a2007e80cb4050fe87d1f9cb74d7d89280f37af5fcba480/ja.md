```
initial(::Type{RandomInitialLayout}, N::T) where {T <: EcologicalNetworks.AbstractEcologicalNetwork}
```

ノードを円形にランダムに配置します。これは、任意の力指向レイアウトの良い出発点です。円は、ネットワークの豊かさの平方根の2倍の半径になるようにスケーリングされており、ほとんどのレイアウトがより早く収束するのに役立ちます。
