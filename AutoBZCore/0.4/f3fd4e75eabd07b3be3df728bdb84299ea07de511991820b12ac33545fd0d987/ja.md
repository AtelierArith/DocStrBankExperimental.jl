```
CommonSolveIntegralFunction(prob, alg, update!, postsolve, [prototype, specialize]; kws...)
```

CommonSolve.jlインターフェースで定義された問題`prob`を解くための被積分関数のコンストラクタで、`init(prob, alg; kws...)`を使用してインスタンス化されます。ヘルパー関数には、`update!(cache, x, p)`が`solve!(cache)`の前に呼び出され、その後に`postsolve(sol, x, p)`が続き、解の値を返す必要があります。`prototype`引数は、問題の型にどれだけ`specialize`するかを制御するのに役立ち、デフォルトは`FullSpecialize()`で、実行時間が改善されます。ただし、`FunctionWrapperSpecialize()`はコンパイル時間を短縮するのに役立つかもしれません。
