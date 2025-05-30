```julia
PardisoJL(; nprocs::Union{Int, Nothing} = nothing,
    solver_type = nothing,
    matrix_type = nothing,
    iparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    dparm::Union{Vector{Tuple{Int, Int}}, Nothing} = nothing,
    vendor::Union{Symbol, Nothing} = nothing
)
```

Pardisoを使用した汎用メソッドです。`solver_type`の指定が必要です。

!!! note
    このソルバーを使用するには、Pardiso.jlパッケージを追加する必要があります。すなわち、`using Pardiso`です。


## キーワード引数

`vendor`キーワードを使用すると、Panua pardiso（旧pardiso-project.org; `vendor=:Panua`）とMKL Pardiso（`vendor=:MKL`）の間で選択できます。`vendor==nothing`の場合、Panua pardisoがMKL Pardisoよりも優先されます。

他のキーワード引数の定義については、Pardiso.jlのドキュメントを参照してください。すべての値はデフォルトで`nothing`となり、ソルバーは入力タイプに基づいて値を内部的に決定します。これらのキーワード引数はデフォルトの処理プロセスを上書きするためのものであり、ほとんどのユーザーには必要ないはずです。
