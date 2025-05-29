```
simulator_config(sim; info_level = 3, linear_solver = GenericKrylov())
```

[`simulate!`](@ref) に渡すことができるシミュレーター設定オブジェクトをセットアップします。

特定のシミュレーターを構成するための多くのオプションがあります。これらの可能な構成オプションの概要を把握する最良の方法は、引数なしで設定をインスタンス化し、REPL で `simulator_config(sim)` を呼び出して結果のテーブルを調べることです。
