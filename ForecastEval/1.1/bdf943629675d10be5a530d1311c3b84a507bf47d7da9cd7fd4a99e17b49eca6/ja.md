```
dm(lossdiff::Vector{<:Number}, dmmethod ; kwargs...)
```

この関数は、Diebold, Mariano (1995) "Comparing Predictive Accuracy" で提案されたテストを実装しています。

x*1 を予測 1、x*2 を予測 2、y を予測ターゲットとします。L(., .) を損失関数とします。最初の引数 lossdiff は、次の操作によって作成されたベクトルであると仮定されます：

L(x*1, y) - L(x*2, y)

2 番目の引数 dmmethod は、現在 DMHAC または DMBoot の明示的なメソッドタイプであることができます（詳細については ?DMHAC および ?DMBoot を参照してください）。この場合、キーワード引数は必要ありません。

あるいは、dmmethod は、ユーザーが HAC メソッドまたはブートストラップメソッドを使用したいかどうかに応じて、シンボル :hac または :boot に設定できます。この場合、提供されたキーワード引数は DMHAC または DMBoot コンストラクタに渡されます（詳細については ?DMHAC および ?DMBoot を参照してください）。

最後に、2 番目の引数は完全に省略することができ、その場合、メソッドはデフォルトのブートストラップメソッドにデフォルト設定されます。これは、Politis と Romano (1993) による定常ブートストラップで、ブロック長は Patton, Politis, および White (2009) に従って推定されます。

Diebold-Mariano テストの出力は DMTest 型です。詳細については ?DMTest を使用してください。
