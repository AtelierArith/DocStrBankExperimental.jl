```julia
PanuaPardisoIterate(; nprocs::Union{Int, Nothing} = nothing,
    matrix_type = nothing,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing)
```

Panua Pardisoを使用した混合因子分解+反復法です。

!!! note
    このソルバーを使用するには、Pardiso.jlパッケージを追加する必要があります。すなわち、`using Pardiso`


## キーワード引数

キーワード引数の定義については、Pardiso.jlのドキュメントを参照してください。すべての値はデフォルトで`nothing`に設定されており、ソルバーは入力タイプに基づいて内部的に値を決定します。これらのキーワード引数は、デフォルトの処理を上書きするためのものであり、ほとんどのユーザーには必要ないはずです。
