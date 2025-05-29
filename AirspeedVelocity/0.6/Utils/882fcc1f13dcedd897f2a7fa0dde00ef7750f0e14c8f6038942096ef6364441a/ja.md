```
benchmark(package_specs::Union{PackageSpec,Vector{PackageSpec}}; output_dir::String=".", script::Union{String,Nothing}=nothing, tune::Bool=false, exeflags::Cmd=``, extra_pkgs::Vector{String}=String[])
```

指定されたJuliaパッケージのベンチマークを実行します。

この関数は、`package_spec`で定義されたパッケージの`script`に指定されたベンチマークを実行します。`script`が提供されていない場合、関数は`{PACKAGE_SRC_DIR}/benchmark/benchmarks.jl`にあるデフォルトのベンチマークスクリプトを使用します。

ベンチマークは、ベンチマークスクリプトで定義された`SUITE`変数を使用して実行され、これはBenchmarkTools.BenchmarkGroup型である必要があります。ベンチマークは、`tune`引数の値に応じて、チューニングありまたはなしで実行できます。

ベンチマークの結果は、指定された`output_dir`に`results_packagename@rev.json`という名前のJSONファイルに保存されます。

# 引数

  * `package::Union{PackageSpec,Vector{PackageSpec}}`: ベンチマークを実行するパッケージに関する情報を含むパッケージ仕様。複数のバージョンのパッケージのベンチマークを実行するために、パッケージ仕様のベクターを渡すこともできます。
  * `output_dir::String="."`: ベンチマーク結果のJSONファイルが保存されるディレクトリ（デフォルト: 現在のディレクトリ）。
  * `script::Union{String,Nothing}=nothing`: ベンチマークスクリプトファイルのパス。提供されない場合、`{PACKAGE}/benchmark/benchmarks.jl`のデフォルトスクリプトが使用されます。
  * `tune::Bool=false`: チューニングありでベンチマークを実行するかどうか（デフォルト: false）。
  * `exeflags::Cmd=```: ベンチマークスクリプトを実行するための追加の実行フラグ（デフォルト: 空）。
  * `extra_pkgs::Vector{String}=String[]`: ベンチマーク環境に追加するパッケージ。
  * `benchmark_on::Union{String,Nothing}=nothing`: ベンチマークスクリプトファイルをダウンロードする場合、使用するリビジョンを指定します。
  * `filter_benchmarks::Vector{String}=String[]`: 実行するベンチマークをフィルタリング（デフォルト: すべて）。
  * `nsamples_load_time::Int=5`: 読み込み時間ベンチマークのために取得するサンプル数。
