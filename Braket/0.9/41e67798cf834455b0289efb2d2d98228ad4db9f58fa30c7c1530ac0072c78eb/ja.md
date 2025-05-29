```
@hybrid_job [device] [job_creation_kwargs] job_function(args...; kwargs..)
```

`job_function`を[Amazon Braket Job](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs.html)内で実行し、`job_creation_kwargs`で定義された作成引数を使用してジョブを起動し、デバイス`device`を予約します（空の場合は`local:local/none`が使用されます）。`device`は、[有効なAWSデバイスARN](https://docs.aws.amazon.com/braket/latest/developerguide/braket-devices.html)であるか、`local:<simulator_provider>/<simulator_name>`の形式を使用する必要があります（[埋め込みシミュレーター](https://docs.aws.amazon.com/braket/latest/developerguide/pennylane-embedded-simulators.html)に関する開発者ガイドを参照してください）。

有効なジョブ作成キーワード引数は次のとおりです：     - `jl_dependencies::String`: `job_function`を実行するために必要なJuliaパッケージを含む`Project.toml`へのパス。`""`（デフォルト）にすることができます。     - `py_dependencies::String`: `job_function`を実行するために必要なPythonパッケージを含む`requirements.txt`へのパス。`""`（デフォルト）にすることができます。     - `as_local::Bool`: [ローカルモード](https://docs.aws.amazon.com/braket/latest/developerguide/braket-jobs-local-mode.html)でジョブを実行するかどうか。デフォルトは`false`で、ハイブリッドの非ローカルジョブとして実行されます。     - `include_modules`: 使用されていませんが予約された引数です。     - `using_jl_pkgs::Union{String, Vector{String}}`: ジョブ内で`job_function`が呼び出される前に`using [pkgs]`でロードするJuliaパッケージ。     - `include_jl_files::Union{String, Vector{String}}`: `job_function`が呼び出される前に`include(file)`でロードするJuliaファイルへのパス。     - [`AwsQuantumJob`](@ref)の作成引数

現在、`job_function`への`args`と`kwargs`は`JLD2.jl`によってシリアライズ可能でなければなりません。`job_function`はJulia関数であり、Pythonではありません。

!!! note
    ファイルと依存関係を含めるためのパスは、このマクロの*呼び出し位置*から解決されます - パスが正しく解決されることを保証するために、相対パスではなく絶対パスを使用してください。


# 例

```julia
function my_job_func(a, b::Int; c=0, d::Float64=1.0, kwargs...)
    Braket.save_job_result(job_helper())
    py_reqs = read(joinpath(Braket.get_input_data_dir(), "requirements.txt"), String)
    hyperparameters = Braket.get_hyperparameters()
    write("test/output_file.txt", "hello")
    return 0
end

py_deps = joinpath(@__DIR__, "requirements.txt")
jl_deps = joinpath(@__DIR__, "JobProject.toml")
input_data = joinpath(@__DIR__, "requirements")
include_jl_files = joinpath(@__DIR__, "job_test_script.jl")

j = @hybrid_job Braket.SV1() wait_until_complete=true as_local=false include_modules="job_test_script" using_jl_pkgs="LinearAlgebra" include_jl_files=include_jl_files py_dependencies=py_deps jl_dependencies=jl_deps input_data=input_data my_job_func(MyStruct(), 2, d=5.0, extra_kwarg="extra_value")
```
