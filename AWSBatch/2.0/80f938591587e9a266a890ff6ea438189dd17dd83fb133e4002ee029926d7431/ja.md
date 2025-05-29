```
run_batch(;
    name::AbstractString="",
    queue::AbstractString="",
    region::AbstractString="",
    definition::Union{AbstractString, JobDefinition, Nothing}=nothing,
    image::AbstractString="",
    vcpus::Integer=1,
    memory::Integer=-1,
    role::AbstractString="",
    cmd::Cmd=``,
    num_jobs::Integer=1,
    parameters::Dict{String, String}=Dict{String, String}(),
) -> BatchJob
```

さまざまな潜在的なデフォルトに基づいてBatchJobを提出する処理を行います。たとえば、デフォルトのジョブフィールドは、既存のジョブ定義または既存のジョブ（現在バッチジョブで実行中の場合）から推測できます。

優先順位の順序は、最も高いものから最も低いものまで次のとおりです。

1. `kwargs`を介して渡された明示的な引数。
2. 推測された環境（例：`AWS_BATCH_JOB_ID`環境変数が設定されている）
3. ジョブ定義パラメータ

有効なジョブ定義が存在しない場合（[`AWSBatch.job_definition_arn`](@ref)を参照）、ジョブパラメータに基づいて新しいジョブ定義が作成され、登録されます。
