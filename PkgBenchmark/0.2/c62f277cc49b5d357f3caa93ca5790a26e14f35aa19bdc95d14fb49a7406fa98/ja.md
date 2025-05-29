```
judge(pkg::Union{Module, String},
      [target]::Union{String, BenchmarkConfig},
      baseline::Union{String, BenchmarkConfig};
      kwargs...)
```

**引数**:

  * `pkg` - ベンチマークするパッケージ。パッケージモジュール、名前、またはディレクトリのいずれか。
  * `target` - judgeに渡すもので、git idまたは[`BenchmarkConfig`](@ref)として指定します。省略した場合は、パッケージリポジトリの現在の状態を使用します。
  * `baseline` - `target`と比較するコミット / [`BenchmarkConfig`](@ref)。

**キーワード引数**:

  * `f` - [judging](https://github.com/JuliaCI/BenchmarkTools.jl/blob/master/doc/manual.md#trialratio-and-trialjudgement)に使用する推定関数。
  * `judgekwargs::Dict{Symbol, Any}` - BenchmarkToolsの`judge`関数に渡すキーワード引数。

残りのキーワード引数は[`benchmarkpkg`](@ref)に渡されます。

**戻り値**:

[`BenchmarkJudgement`](@ref)を返します。
