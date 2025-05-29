```
CPU1()
CPU1(settings)
```

計算がCPUのシングルスレッドモードで実行されるべきであることを示します。オプションで、アルゴリズム設定を指定するオブジェクトを渡すことができます。

# 例:

```julia
filter(CPU1(), image, kernel)
filter(CPU1(TileSize(64,8)), image, kernel)
```
