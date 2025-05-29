```
CommonSolveFourierIntegralFunction(prob, alg, update!, postsolve, s, [prototype, specialize]; alias=false, kws...)
```

CommonSolve.jlインターフェースで定義された問題`prob`を解決するための被積分関数のコンストラクタで、`init(prob, alg; kws...)`を使用してインスタンス化されます。ヘルパー関数には、`update!(cache, x, s(x), p)`が`solve!(cache)`の前に呼び出され、その後に`postsolve(sol, x, s(x), p)`が呼び出され、解の値を返す必要があります。`prototype`引数は、問題の型にどれだけ`specialize`するかを制御するのに役立ち、デフォルトは`FullSpecialize()`で、実行時間が改善されます。ただし、`FunctionWrapperSpecialize()`はコンパイル時間を短縮するのに役立つかもしれません。
