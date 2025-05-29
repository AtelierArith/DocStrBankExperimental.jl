```
solve(i::CombinatorialInstance, algo::CombinatorialAlgorithm)
```

与えられた組合せインスタンス `i` を提供されたアルゴリズム `algo` を使用して解決します（解決プロセスのためのパラメータを含む可能性があります）。返される値は `CombinatorialSolution` です。

要求されたアルゴリズムがこのタイプのインスタンスに対して利用できない場合、`MethodError` がスローされます。
