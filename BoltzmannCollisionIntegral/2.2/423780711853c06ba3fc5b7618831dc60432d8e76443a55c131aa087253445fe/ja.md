```
SpectraEvaluateMultiThread(userInputMultiThread)
```

マルチスレッド環境でSおよびT配列のモンテカルロ積分を実行する関数です。この関数は、グローバル変数nThreadsで指定されたスレッド数にわたってモンテカルロ積分を並行して実行します。その後、SおよびT行列を計算し、結果をファイルに保存します。
