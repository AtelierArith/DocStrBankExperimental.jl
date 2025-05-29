```julia
setup_mpi(; args...)

```

まず、`Pigeons.setup_mpi_`と入力してタブを押すことで、"プリセット"が利用可能なクラスターのリストを確認してください。これらは最も使いやすいものです。

プリセットが利用できない場合は、`setup_mpi()`を使用してください。`setup_mpi()`の引数のドキュメントを見るには、[`MPISettings`](@ref)を参照してください（つまり、`args...`は[`MPISettings`](@ref)のコンストラクタに渡されます）。

新しい"プリセット"関数`Pigeons.setup_mpi_...()`を追加したい場合は、`Pigeons/src/submission/presets.jl`へのプルリクエストを歓迎します。
