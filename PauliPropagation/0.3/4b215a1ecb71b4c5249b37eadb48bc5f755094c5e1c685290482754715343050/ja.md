```
AmplitudeDampingNoise(qind::Int, gamma::Real)
```

インデックス `qind` のキュービットに作用する凍結された振幅減衰ノイズチャネルで、ノイズ強度は `gamma` です。XおよびYパウリを減衰させ、ZをIおよびZ成分に分割します（転置ハイゼンベルク画像において）。
