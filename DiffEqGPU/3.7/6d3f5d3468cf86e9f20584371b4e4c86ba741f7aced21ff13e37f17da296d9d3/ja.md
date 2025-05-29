```julia
EnsembleCPUArray(cpu_offload = 0.2)
```

`EnsembleArrayAlgorithm`は、各ODEソルブをそれぞれのODEインテグレーターで並列化するためにCPUカーネルを利用します。このメソッドは、`EnsembleGPUArray`のデバッグ用の対となるものであり、同じ動作を持ち、結合されたODEを構築するために同じKernelAbstractions.jlプロセスを使用しますが、`f`がGPU互換のカーネル関数であるという制約はありません。

このメソッドは、ライブラリの開発やデバッグを超えて有用である可能性は低く、ほとんどのケースでは`EnsembleThreads`や`EnsembleDistributed`の方が速いはずです。
