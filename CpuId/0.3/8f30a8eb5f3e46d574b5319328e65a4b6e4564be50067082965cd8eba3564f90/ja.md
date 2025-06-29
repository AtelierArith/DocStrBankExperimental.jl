```
cpucores()
```

現在実行中のCPUの物理コアの数を`cpuid`命令を呼び出すことで決定します。複数のCPUを持つシステムでは、これはコードを実行している単一のCPUに関する情報のみを提供します。この機能のクエリがサポートされていない場合はゼロを返します。これは、実行中のハイパーバイザーによるものである可能性もあります（hvvendor() == :Microsoftで観察されるように）。

また、この関数は論理コア（別名ハイパースレッディング）を考慮せず、通常はL3キャッシュとメインメモリ帯域幅を共有する真の物理コアの数を決定します。

マシン上のすべての論理コアの合計数を提供するJuliaのグローバル変数`Base.Sys.CPU_THREADS`も参照してください。
