```
PkgBenchmark(; file="~/.julia/packages/PkgTemplates/MepaC/templates/benchmark/benchmarks.jlt")
```

[PkgBenchmark.jl](https://github.com/JuliaCI/PkgBenchmark.jl) ベンチマークスイートを設定します。

ベンチマークの再現性を確保するために、`benchmark` サブフォルダーに手動で環境を作成する必要があります（このために `Manifest.toml` はバージョン管理にコミットされています）。この環境では、少なくとも次のことを行う必要があります：

  * `pkg> add BenchmarkTools`
  * `pkg> dev` あなたの新しいパッケージ。

## キーワード引数

  * `file::AbstractString`: `benchmarks.jl` のテンプレートファイル。
