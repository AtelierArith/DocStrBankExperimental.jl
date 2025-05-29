```
interpolate(layer::SDMLayer; dest="+proj=natearth2", newsize=nothing)
```

新しい宛先CRS（デフォルトはnatearth2）に基づいてレイヤーの補間されたバージョンを返し、オプションで`newsize`の新しいサイズを指定できます。
