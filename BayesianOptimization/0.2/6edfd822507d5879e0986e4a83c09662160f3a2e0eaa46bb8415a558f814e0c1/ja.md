```
ScaledSobolIterator(lowerbounds, upperbounds, N;
                    seq = SobolSeq(length(lowerbounds)))
```

`lowerbounds` と `upperbounds` の間の Sobol シーケンスの `N` 要素を返すイテレータを返します。Sobol シーケンスの最初の `N` 要素は、より良い一様性のためにスキップされます (https://github.com/stevengj/Sobol.jl を参照)。
