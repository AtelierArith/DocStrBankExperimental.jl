```
fine_mixed_cells(f::Vector{<:MP.AbstractPolynomialLike}; show_progress=true, max_tries = 10)
fine_mixed_cells(support::Vector{<:Matrix}; show_progress=true, max_tries = 10)
```

与えられた `support` によって誘導されるすべての（ファイン）混合セルを計算します。これにより、すべての誘導された初期形式が二項式であることが保証されます。選択されたリフティングが一般的でない場合、アルゴリズムは再起動されます。これは最大で `max_tries` 回まで発生します。すべての混合セルと対応するリフティングの `Vector` を返すか、アルゴリズムがファイン混合セルを計算できなかった場合は `nothing` を返します。これは、現在の技術的制限のために発生する可能性があります。
