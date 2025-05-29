```
OptimizationOptions(; 
θopt = OptimOptionsθ(), 
δopt = OptimOptionsδ(), 
threads = GrumpsThreads(), 
memsave = false, 
maxrepeats = 4, 
probtype = :fast,
id = :Grumps,
progressbar = false,
loopvectorization = true
)
```

数値最適化に使用されるオプションを設定します。 *θopt* は外部最適化ルーチンに使用され、*δopt* は内部のものに使用されます。これらはどちらも *OptimOptions* 型です。詳細については *OptimOptionsθ* および *OptimOptionsδ* メソッドを参照してください。 *memsave* 変数はデフォルトで false に設定されています。これをオンにするとメモリ消費が大幅に削減されますが、計算が遅くなります。変数 *maxrepeats* は将来的に消える可能性があります。

選択確率を計算する方法は二つあります：ロバストとファストで、*probtype* に *:robust* または *:fast* を渡すことで指定します。ファスト選択確率は良い理由からデフォルトです。

プログレスバーは、画面の右上隅に色付きの円の形でイテレーション内の進捗を示します。プログレスバーはデフォルトでオフになっており、Grumps がターミナルなしで実行される場合（例：PBS や Slurm でのバッチスクリプト実行）にはオフにしておくべきです。ループベクトル化は Grumps への新しい追加であり、ほとんどの場合計算を高速化します。

最後に、id を指定することでコールバックを追加できます。例えば、各内部および外部イテレーションで呼び出されるユーザー関数です。ドキュメントの [Extending Grumps](@ref) 部分を参照してください。
