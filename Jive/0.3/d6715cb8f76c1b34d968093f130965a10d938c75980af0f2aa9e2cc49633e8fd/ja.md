```
runtests(dir::String ;
         failfast::Bool = false,
         targets::Union{AbstractString, Vector{<: AbstractString}} = String[],
         skip::Union{Vector{Any}, Vector{<: AbstractString}} = String[],
         testset::Union{Nothing, AbstractString, Vector{<: AbstractString}, Regex, Base.Callable} = nothing,
         context::Union{Nothing, Module} = nothing,
         enable_distributed::Bool = true,
         node1::Union{Vector{Any}, Vector{<: AbstractString}} = String[],
         verbose::Bool = true)::Total
```

特定のディレクトリからテストファイルを実行します。

  * `dir`: 探索するルートディレクトリ。
  * `failfast`: 最初の失敗で中止します。`ENV`変数`JULIA_TEST_FAILFAST`が設定されている場合は上書きされます。
  * `targets`: 対象をフィルタリングして開始します。``(スペース)で区切られた`String`または`Vector{String}`。`ARGS`が空でない場合は上書きされます。
  * `skip`: スキップするファイルまたはディレクトリ。`ENV`変数`JIVE_SKIP`が設定されている場合は上書きされます。`,`(カンマ)で区切られます。
  * `testset`: テストセットをフィルタリングします。デフォルトは`nothing`です。
  * `context`: `Base.include`で使用されるモジュール。`nothing`は、すべてのテストファイルに対して匿名モジュールを使用することが安全であることを意味します。
  * `enable_distributed`: 分散のオプション。`ENV`変数`JIVE_PROCS`が設定されている場合は上書きされます。
  * `node1`: 分散テスト中にノード1で実行します。
  * `verbose`: テスト実行の詳細を印刷します。
