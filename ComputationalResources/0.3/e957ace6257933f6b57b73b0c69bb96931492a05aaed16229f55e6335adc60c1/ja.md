```
CPUProcesses()
CPUProcesses(settings)
```

計算がマルチプロセスモードでCPUを使用して実行されるべきことを示します。プロセスはaddprocs()を使用して追加するか、`julia -p N`で起動されたjuliaで追加する必要があります。プロセスはリモート参照などの分散メモリ操作を使用して通信する必要があります。オプションで、アルゴリズム設定を指定するオブジェクトを渡すことができます。

# 例:

```julia
filter(CPUProcesses(), image, kernel)
filter(CPUProcesses(TileSize(64,8)), image, kernel)
```
