```
cputhreads()
```

現在実行中のCPUの論理コアの数を、`cpuid`命令を呼び出すことで決定します。複数のCPUを持つシステムでは、これはコードを実行している単一のCPUに関する情報のみを提供します。この機能のクエリがサポートされていない場合はゼロを返します。これは、実行中のハイパーバイザーが原因である可能性もあります（hvvendor() == :Microsoftで観察されるように）。

`cpucores()`とは対照的に、この関数は論理コア、つまりハイパースレッディングも考慮に入れます。実用的な目的では、I/O集約型のコードのみがこれらのコアの総数を利用すべきです。メモリまたは計算に制約のあるコードは恩恵を受けず、むしろ悪影響を受けるでしょう。

また、マシン上のすべての論理コアの合計数を提供するJuliaのグローバル変数`Base.Sys.CPU_THREADS`も参照してください。したがって、`Base.Sys.CPU_THREADS ÷ CpuId.cputhreads()`は、システム内のCPU（パッケージ）の数を示すはずです。
