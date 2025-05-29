```
RecurrenceMatrix(x, rthres; metric = Euclidean(), parallel::Bool)
```

時系列または軌道 `x` から再帰行列を作成し、再帰閾値 `rthres` を設定します。`x` は多変量データのための [`StateSpaceSet`](@ref) であるか、時系列のための `AbstractVector{<:Real}` です。

変数 `rthres` は再帰がどのように推定されるかを定義します。これは [`AbstractRecurrenceType`](@ref) の任意のサブタイプであり、異なるタイプは異なる方法で再帰を指定できます。あるいは、`rthres` は実数であり、その場合は [`RecurrenceThreshold`](@ref) のインスタンスになります。

キーワード `metric` は、指定された場合、[Distances.jl](https://github.com/JuliaStats/Distances.jl) の `Metric` の任意のサブタイプでなければならず、再帰のための距離を計算するために使用されるメトリックを定義します。デフォルトではユークリッド距離が使用され、一般的な代替として `Chebyshev(), Cityblock()` があります。

キーワード `parallel` は、計算がスレッドを使用して並列に行われるべきかどうかを決定します。デフォルトは `length(x) > 500 && Threads.nthreads() > 1` です。

## 説明

（クロス）再帰行列は、軌道で発生する*再帰*を定量化する方法です。再帰は、軌道が以前のある時点でいた状態空間の同じ近傍を訪れるときに発生します。

再帰行列は、再帰プロットの数値表現であり、詳細は [^Marwan2007] および [^Marwan2015] で説明されています。これは、軌道における再帰を定量化するブール値の疎な正方行列を表します。すなわち、軌道が自身に近い場所に戻る点です。軌道 `x, y` が与えられ、`ε` が Real であると仮定すると、行列は次のように定義されます：

```julia
R[i,j] = metric(x[i], y[i]) ≤ ε ? true : false
```

ここで `metric` は距離関数です。`RecurrenceMatrix` と [`CrossRecurrenceMatrix`](@ref) の違いは、前者の場合 `x === y` であることです。

`<:AbstractRecurrenceMatrix` 型のオブジェクトは [`recurrenceplot`](@ref) として表示されます。

また、[`CrossRecurrenceMatrix`](@ref)、[`JointRecurrenceMatrix`](@ref) も参照し、これらの関数の結果をプロット可能な形式に変換するために [`recurrenceplot`](@ref) を使用してください。

[^Marwan2007]: N. Marwan *et al.*, "Recurrence plots for the analysis of complex systems", [Phys. Reports 438*(5-6), 237-329 (2007)](https://doi.org/10.1016/j.physrep.2006.11.001)

[^Marwan2015]: N. Marwan & C.L. Webber, *Recurrence Quantification Analysis. Theory and Best Practices* [Springer (2015)](https://link.springer.com/book/10.1007/978-3-319-07155-8)
