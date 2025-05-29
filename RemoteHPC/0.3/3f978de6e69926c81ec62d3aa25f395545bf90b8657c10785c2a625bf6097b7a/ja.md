```
Exec(;name::String = "",
      path::String = "",
      flags::Dict = Dict(),
      modules::Vector{String} = String[],
      parallel::Bool = true)
```

実行可能ファイルの表現。任意の [`Storable`](@ref) と同様に、`name` は単にラベルとして使用され、[`Server`](@ref) からそれを [`load`](@ref) できるようにします。

ジョブスクリプトでは、これは `<path> <flags>` に変換されます。

# `configure()` の例

```julia
name::String = "exec_label"
path::String = "/path/to/exec"
flags::Dict{Any, Any} = Dict{Any, Any}("l" => 1, "-np" => 4, "trialname" => "testtrial")
modules::Vector{String} = String["intel","intel-mkl"]
parallel::Bool = false
```

# 例:

```julia
Exec(; path="ls", flags=Dict("l" => ""))
```

はジョブスクリプトで `ls -l` に変換されます。

# フラグ

`flags` `Dict` は次のようにジョブスクリプトに展開されます：

```julia
Exec(path="foo", flags = Dict("N"    => 1,
                              "-nk"  => 10,
                              "np"   => "$NPOOLS",
                              "--t"  => "",
                              "--t2" => 24)
# は次のように変換されます: foo -N1 -nk 10 --np=$NPOOLS --t --t2=24
```

# モジュール

`modules` ベクターは `module load` コマンドに展開されます：`modules = ["gcc", "QuantumESPRESSO"]` はジョブスクリプトで `module load gcc, QuantumESPRESSO` になります。

# 並列

`parallel` は、実行可能ファイルが実行環境を表す [`Environment`](@ref) で定義された並列実行可能ファイルで実行されるべきかどうかを伝えます。例えば：

```julia
# ジョブの環境が次のように定義されている場合：
Environment(parallel_exec=Exec(path="srun"))
# 次の Exec は：
Exec(path="foo", parallel=true)
# は次のように変換されます: srun foo
```
