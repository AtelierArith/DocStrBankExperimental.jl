```
KPMExpansion(func::Function, bounds, M::Int, N::Int = 2*M)
```

[`KPMExpansion`](@ref) 型のインスタンスを初期化して、単変数関数 `func` を近似します。`func` は `func(x)` として呼び出され、区間 `bounds[1] < x < bounds[2]` での M 次のチェビシェフ多項式展開を行います。ここで、`N ≥ M` は指定された区間で `func` が評価される点の数であり、これらの点はチェビシェフ-ガウス数値積分を通じて展開係数を計算するために使用されます。
