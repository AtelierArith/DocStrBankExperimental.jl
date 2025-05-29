```julia
MKLPardisoIterate(; nprocs::Union{Int, Nothing} = nothing,
    matrix_type = nothing,
    cache_analysis = false,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing)
```

MKL Pardisoを使用した混合因子分解+反復法。

!!! note
    このソルバーを使用するには、Pardiso.jlパッケージを追加する必要があります。すなわち、`using Pardiso`


## キーワード引数

`cache_analysis = true`を設定すると、Pardisoのスケーリングとマッチングのデフォルトが無効になり、このソルバーを使用したすべてのさらなる計算のために初期分析フェーズの結果がキャッシュされます。

他のキーワード引数の定義については、Pardiso.jlのドキュメントを参照してください。すべての値はデフォルトで`nothing`になっており、ソルバーは入力タイプに基づいて値を内部的に決定します。これらのキーワード引数は、デフォルトの処理プロセスをオーバーライドするためのものであり、ほとんどのユーザーには必要ないはずです。
