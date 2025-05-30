```
layers(::Type{AbstractSatellite})
layers(x::AbstractSatellite)
```

指定されたセンサーに対して利用可能なすべてのレイヤーの名前を返します。

# 例

```julia
# Landsat 8のすべての利用可能なレイヤーを取得
landsat_layers = layers(Landsat8)

# 特定のシーンのすべての利用可能なレイヤーを取得
src = Landsat8("LC08_L2SP_043024_20200802_20200914_02_T1")
available_layers = layers(src)
```
