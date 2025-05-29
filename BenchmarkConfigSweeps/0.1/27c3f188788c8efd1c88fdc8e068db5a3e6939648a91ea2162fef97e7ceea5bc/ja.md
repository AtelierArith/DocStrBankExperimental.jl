# BenchmarkConfigSweeps

BenchmarkConfigSweeps.jlは、さまざまな`--nthreads`設定、環境変数、および`julia`バージョンに対してベンチマークを実行するために使用できます。

各構成は、`BenchmarkConfigSweeps.nthreads`、`BenchmarkConfigSweeps.env`、および`BenchmarkConfigSweeps.julia`などの構成指定子の組み合わせとして指定されます。ベンチマークを実行するための構成のセットは、単にそのような構成指定子の（タプルの）反復可能なものです：

```JULIA
using BenchmarkConfigSweeps

nthreads_list = [1, 4, 8, 16]
configs = Iterators.product(
    zip(
        BenchmarkConfigSweeps.nthreads.(nthreads_list),
        BenchmarkConfigSweeps.env.("OPENBLAS_NUM_THREADS" .=> nthreads_list),
    ),
    BenchmarkConfigSweeps.env.(
        "JULIA_PROJECT" .=> ["baseline", "target"],
        "JULIA_LOAD_PATH" => "@",  # 変化しない
    ),
    BenchmarkConfigSweeps.julia.(["julia1.5", "julia1.6"]),
)
```

その後、`BenchmarkConfigSweeps.run`に渡すことができます：

```JULIA
BenchmarkConfigSweeps.run("build", "benchmarks.jl", configs)
```

ここで、`"build"`は結果を保存するディレクトリであり、`"benchmarks.jl"`はトップレベルで変数`SUITE :: BenchmarkGroup`を定義するJuliaスクリプトです。

結果は次のようにして読み込むことができます：

```JULIA
sweepresult = BenchmarkConfigSweeps.load("build")
```

`sweepresult`オブジェクトはTables.jlインターフェースを実装しています。たとえば、次のようにして簡単に`DataFrame`に変換できます：

```JULIA
using DataFrames
df = DataFrame(sweepresult)
```

デフォルトのテーブル変換は、`BenchmarkGroup`キーの意味を推測しようとするため、ややDWIM的であることに注意してください。詳細については、`BenchmarkConfigSweeps.flattable`を参照してください。プログラムによる処理には`BenchmarkConfigSweeps.simpletable`を使用してください。
