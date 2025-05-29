```
Coordinates(layer::E; coords = [(rand(), rand()) for _ = 1:20]) where E<:EnvironmentLayer
```

単一のEnvironmentLayerから環境変数が構築され、オプションで座標のセットをキーワード引数として渡すことができる`Coordinates`を構築します。
