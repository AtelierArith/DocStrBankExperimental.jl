```
Job(name::String, structure::Structure;
      calculations      ::Vector{Calculation} = Calculation[],
      dir               ::String = pwd(),
      version           ::Int = last_job_version(dir),
      copy_temp_folders ::Bool = false, 
      server            ::String = getdefault_server(),
      environment::String ="")
```

A [`Job`](@ref) は、`dir` ディレクトリ内で実行される一連の [`Calculations`](@ref Calculation) を具現化し、[`Structure`](@ref) を対象とします。

## キーワード/さらなる属性

  * `calculations`: 逐次実行される計算。
  * `dir`: 計算が実行されるディレクトリ。
  * `version`: ジョブの現在のバージョン。
  * `copy_temp_folders`: 中間計算結果に関連する一時ディレクトリをジョブバージョンを保存する際にコピーするかどうか。*注意* これらはかなり大きくなる可能性があります。
  * `server`: [`Server`](@ref) で [`Job`](@ref) を実行する場所。
  * `environment`: [`Job`](@ref) を実行するために使用される [`Environment`](@ref)。

```
Job(job_name::String, structure::Structure, calculations::Vector{<:Calculation}, common_flags::Pair{Symbol, <:Any}...; kwargs...)
```

新しいジョブを作成します。共通フラグは各 `calculations` に設定されるように試みられます。`kwargs...` は [`Job`](@ref) コンストラクタに渡されます。

```
Job(job_dir::String, job_script="job.sh"; version=nothing, kwargs...)
```

`dir` 内のジョブをロードします。`job_dir` が有効なジョブパスでない場合、以前に保存されたジョブが `job_dir` を部分的に含む `dir` を持つジョブをスキャンします。`version` が指定されている場合、対応するジョブバージョンが存在すれば返されます。`kwargs...` は [`Job`](@ref) コンストラクタに渡されます。
