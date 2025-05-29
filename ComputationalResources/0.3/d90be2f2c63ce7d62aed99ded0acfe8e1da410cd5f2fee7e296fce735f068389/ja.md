```
CPUThreads()
CPUThreads(settings)
```

計算をCPUのマルチスレッドモードで実行することを示します。オプションで、アルゴリズム設定を指定するオブジェクトを渡すことができます。

# 例:

```julia
filter(CPUThreads(), image, kernel)
filter(CPUThreads(TileSize(64,8)), image, kernel)
```
