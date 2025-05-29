```
run_igblast(
    igblast_type::Type{T},
    query_file::String,
    v_database::String,
    d_database::String,
    j_database::String,
    aux_file::String,
    output_file::String,
    num_threads::Int = Base.Threads.nthreads();
    outfmt::Int = 19,
    additional_params::Dict{String, Any} = Dict()
) where T <: AbstractIgBLAST
```

指定されたパラメータでIgBLASTを実行します。

必須パラメータ:

  * `igblast_type`: 実行するIgBLASTのタイプ（IgBLASTnまたはIgBLASTp）
  * `query_file`: 入力クエリファイルへのパス
  * `v_database`: V遺伝子データベースへのパス
  * `d_database`: D遺伝子データベースへのパス
  * `j_database`: J遺伝子データベースへのパス
  * `aux_file`: 補助ファイルへのパス
  * `output_file`: 出力ファイルへのパス

オプションのパラメータ:

  * `num_threads`: 使用するスレッドの数（デフォルト: 利用可能なすべてのスレッド）
  * `outfmt`: 出力形式（デフォルト: AIRR形式のための19）
  * `additional_params`: 追加のIgBLASTパラメータの辞書

例:

```julia
run_igblast(IgBLASTn, "query.fasta", "V.fasta", "D.fasta", "J.fasta", "aux.txt", "output.txt",
            additional_params = Dict(
                "organism" => "human",
                "domain_system" => "imgt"
            ))
```
