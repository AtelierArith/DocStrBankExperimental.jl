```julia
PanuaPardisoFactorize(; nprocs::Union{Int, Nothing} = nothing,
    matrix_type = nothing,
    cache_analysis = false,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing)
```

Panua Pardisoを使用したスパース因子分解法です。

!!! note
    このソルバーを使用するには、Pardiso.jlパッケージを追加する必要があります。すなわち、`using Pardiso`


## キーワード引数

`cache_analysis = true`を設定すると、Pardisoのスケーリングとマッチングのデフォルトが無効になり、このソルバーでのすべてのさらなる計算のために初期分析フェーズの結果がキャッシュされます。

キーワード引数の定義については、Pardiso.jlのドキュメントを参照してください。すべての値はデフォルトで`nothing`となり、ソルバーは入力タイプに基づいて内部的に値を決定します。これらのキーワード引数は、デフォルトの処理プロセスをオーバーライドするためのものであり、ほとんどのユーザーには必要ないはずです。
