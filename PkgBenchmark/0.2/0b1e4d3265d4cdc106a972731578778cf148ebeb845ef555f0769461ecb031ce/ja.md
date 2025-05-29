```
BenchmarkConfig(;id::Union{String, Nothing} = nothing,
                 juliacmd::Cmd = `joinpath(Sys.BINDIR, Base.julia_exename())`,
                 env::Dict{String, Any} = Dict{String, Any}())
```

`BenchmarkConfig`は、[`benchmarkpkg`](@ref)によって実行されるベンチマークの設定を含みます。

これには以下が含まれます：

  * ベンチマークが実行されるパッケージのコミット。
  * 実行すべきjuliaコマンド、すなわちJulia実行可能ファイルへのパスと

コマンドフラグ（例：`-O`による最適化レベル）。

  * カスタム環境変数（例：`JULIA_NUM_THREADS`）。

コンストラクタは以下のキーワード引数を取ります：

  * `id` - コミット、ブランチ、タグ、"HEAD"、"HEAD~1"などのgit識別子。        `id == nothing`の場合、ベンチマークはリポジトリの現在の状態で行われます        （たとえそれが汚れていても）。
  * `juliacmd` - ベンチマークを実行するために使用され、Pkgbenchmark関数が呼び出されるjulia実行可能ファイルがデフォルトです。コマンドフラグを含めることもできます。
  * `env` - ベンチマークが実行されるときにアクティブになるカスタム環境変数を含みます。

# 例

```julia
julia> using Pkgbenchmark

julia> BenchmarkConfig(id = "performance_improvements",
                       juliacmd = `julia -O3`,
                       env = Dict("JULIA_NUM_THREADS" => 4))
BenchmarkConfig:
    id: performance_improvements
    juliacmd: `julia -O3`
    env: JULIA_NUM_THREADS => 4
```
