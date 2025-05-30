```
benchmarkpkg(pkg, [target]::Union{String, BenchmarkConfig}; kwargs...)
```

パッケージ `pkg` に対して [`BenchmarkConfig`](@ref) または git 識別子 `target` を使用してベンチマークを実行します。git 識別子の例には、コミット SHA、ブランチ名、または e.g. `"HEAD~1"` があります。[`BenchmarkResults`](@ref) を返します。

引数 `pkg` は、パッケージのモジュール、パッケージ名、またはパッケージのルートディレクトリへのパスであることができます。

**キーワード引数**:

  * `script` - ベンチマークのスクリプト。指定しない場合は、パッケージフォルダ内の `benchmark/benchmarks.jl` にデフォルト設定されます。
  * `postprocess` - 結果を後処理するための関数。`BenchmarkGroup` が渡され、それを変更するか、新しいものを返すことができます。
  * `resultfile` - 設定されている場合、出力を `resultfile` に保存します。
  * `retune` - 再調整を強制し、新しい調整をチューンファイルに保存します。
  * `verbose::Bool = true` - 現在実行中のベンチマークを印刷します。
  * `logger_factory` - ベンチマーク中に使用されるロガーを指定します。引数なしでロガーを作成する呼び出し可能オブジェクト（通常は型）でなければなりません。いくつかのパッケージ内の定数として存在する必要があります（例：匿名関数は機能しません）。
  * `progressoptions` - 非推奨。

結果は [`judge`](@ref) のような関数で使用できます。選択した場合、[`writeresults`](@ref) を使用して結果を手動で保存できます。ここで `results` はこの関数の戻り値です。[`readresults`](@ref) を使用して再度読み取ることができます。

**例の呼び出し**:

```julia
using PkgBenchmark

import MyPkg
benchmarkpkg(MyPkg) # リポジトリの現在の状態でベンチマークを実行
benchmarkpkg(MyPkg, "my-feature") # 特定のブランチ/コミット/タグのベンチマークを実行
benchmarkpkg(MyPkg, "my-feature"; script="/home/me/mycustombenchmark.jl")
benchmarkpkg(MyPkg, BenchmarkConfig(id = "my-feature",
                                            env = Dict("JULIA_NUM_THREADS" => 4),
                                            juliacmd = `julia -O3`))
benchmarkpkg(MyPkg,  # ベンチマークを実行し、結果の（中央値）を1000で割る
    postprocess=(results)->(results["g"] = median(results["g"])/1_000)
```
