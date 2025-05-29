```
ReTestItems.runtests()
ReTestItems.runtests(mod::Module)
ReTestItems.runtests(paths::AbstractString...)
```

`@testitem` テストを実行します。

`_test.jl` または `_tests.jl` で終わるファイルのみがテストアイテムを検索されます。

ディレクトリまたはファイルパスが渡された場合、それらのディレクトリとファイルのみが検索されます。引数が渡されない場合、現在のプロジェクトの `src/` および `test/` ディレクトリが `@testitem` を検索します。

# キーワード

## `@testitem` のフィルタリング

  * `name::Union{Regex,AbstractString,Nothing}=nothing`: `@testitem` をその名前でフィルタリングするために使用されます。`AbstractString` 入力は、`name` と正確に一致する `@testitem` のみを保持し、`Regex` は複数の `@testitem` に部分一致するために使用できます。デフォルトでは、フィルタリングは適用されません。
  * `tags::Union{Symbol,AbstractVector{Symbol},Nothing}=nothing`: `@testitem` をそのタグでフィルタリングするために使用されます。単一のタグは、それを含む任意の `@testitem` に一致するために使用でき、複数のタグが提供される場合、すべてのタグを含む `@testitem` のみが実行されます。デフォルトでは、フィルタリングは適用されません。

`name` と `tags` のフィルタは一緒に適用され、両方のフィルタを通過した `@testitem` のみが実行されます。

## `runtests` の設定

  * `testitem_timeout::Real`: `@testitem` が失敗としてマークされるまでの待機秒数。デフォルトは30分です。`RETESTITEMS_TESTITEM_TIMEOUT` 環境変数を使用して設定することもできます。`@testitem` が独自の `timeout` キーワードを設定している場合、それが優先されます。小数値は最も近い秒に切り上げられます。タイムアウトは現在、`nworkers > 0` の場合にのみ適用されることに注意してください。
  * `retries::Int=0`: テストが合格しない場合や、複数のワーカープロセスで実行している場合に、ワーカーが失敗したりタイムアウト制限に達した場合に `@testitem` を再試行する回数。`RETESTITEMS_RETRIES` 環境変数を使用して設定することもできます。`@testitem` が独自の `retries` キーワードを設定している場合、これら2つの再試行回数の最大値がその `@testitem` の再試行制限として使用されます。`report=true` の場合、レポートには再試行された `@testitem` のすべての実行に関する情報が含まれます。
  * `nworkers::Int`: `@testitem` を実行するために使用するワーカープロセスの数。デフォルトは0です。`RETESTITEMS_NWORKERS` 環境変数を使用して設定することもできます。
  * `nworker_threads::Union{String,Int}`: 各ワーカープロセスで使用するスレッドの数。デフォルトは2です。`RETESTITEMS_NWORKER_THREADS` 環境変数を使用して設定することもできます。インタラクティブスレッドは文字列を通じてサポートされています（例: "auto,2"）。
  * `worker_init_expr::Expr`: テストが実行される前に各ワーカープロセスで実行される式。パッケージをロードしたり、環境を設定するために使用できます。`:block` 式でなければなりません。
  * `test_end_expr::Expr`: 各テストアイテムが実行された後に実行される式。テストを実行した後にグローバル状態が変更されていないことを確認するために使用できます。`:block` 式でなければなりません。`test_end_expr` は、テストアイテムが合格、失敗、またはエラーになったかにかかわらず評価されます。`testsetup` が失敗した場合、`test_end_expr` は実行されません。
  * `gc_between_testitems::Bool`: `true` の場合、各テストアイテムが実行された後に完全なガーベジコレクション (GC) が実行されます。デフォルトは `nworkers > 1`、すなわち複数のワーカープロセスで実行している場合は `true` です。複数のワーカープロセスは Julia の GC をトリガーするために調整できないため、ワーカーなしまたは単一のワーカーで実行している場合は直接 GC を呼び出す必要はありません（すべてのテストを実行している単一プロセスによって GC が自動的にトリガーされるため）。`RETESTITEMS_GC_BETWEEN_TESTITEMS` 環境変数を使用して設定することもできます。ヒント: GC を完全に制御するには、`gc_between_testitems=false` に設定し、`test_end_expr` で手動で GC をトリガーします。
  * `memory_threshold::Real`: ワーカープロセスがメモリを解放するために再起動される前に使用できるメモリの割合を設定します。デフォルトは0.99です。`nworkers > 0` の場合のみサポートされています。たとえば、0.8 に設定されている場合、利用可能なメモリの >80% が使用されているときに、ワーカープロセスが終了し、新しいワーカーに置き換えられます。次のテストアイテムは新しいワーカープロセスで実行され、メモリ圧力がしきい値を下回ったかどうかにかかわらず、テストアイテムが実行されます。メモリ圧力がしきい値を上回り続ける場合、次のテストアイテムが実行される前にワーカープロセスが再度置き換えられます。`RETESTITEMS_MEMORY_THRESHOLD` 環境変数を使用して設定することもできます。**注意**: `memory_threshold` キーワードは実験的であり、将来のバージョンで削除される可能性があります。
  * `report::Bool=false`: `true` の場合、テスト結果を要約した JUnit 形式の XML ファイルを書き込みます。`RETESTITEMS_REPORT` 環境変数を使用して設定することもできます。XML レポートが保存される場所は、`RETESTITEMS_REPORT_LOCATION` 環境変数を使用して設定できます。デフォルトでは、レポートはテストされているプロジェクトのルートに書き込まれます。
  * `logs::Symbol`: テスト評価中に生成されたメッセージを表示する方法とタイミングを処理します。次のいずれかになります。

      * `:eager`: すべてが通常の Julia セッションのように即座に `stdout` に印刷されます。
      * `:batched`: ログはファイルに保存され、テストアイテムが終了したときに印刷されます。
      * `:issues`: ログはファイルに保存され、エラーや失敗があった場合にのみ印刷されます。

    インタラクティブセッションの場合、`0` または `1` のワーカープロセスで実行しているときは `:eager` がデフォルトであり、それ以外は `:batched` です。非インタラクティブセッションの場合、デフォルトで `:issues` が使用されます。
  * `verbose_results::Bool`: `true` の場合、最終テストレポートは各 `@testitem` をリストします。それ以外の場合、結果は集約されます。デフォルトは、非インタラクティブセッションまたは `logs=:issues` の場合は `false`、それ以外は `true` です。
  * `validate_paths::Bool=false`: `true` の場合、`runtests` は渡された `paths` のいずれかがテストファイルを含むことができない場合、エラーをスローします。パスが存在しないか、パスがテストファイルでないファイルを指している場合です。デフォルトは `false` です。`RETESTITEMS_VALIDATE_PATHS` 環境変数を使用して設定することもできます。
  * `timeout_profile_wait::Real=0`: 非ゼロの場合、タイムアウトしたワーカーは CPU プロファイルをトリガーし、ワーカーを終了する前に `timeout_profile_wait` 秒待機します。ゼロはプロファイルが取得されないことを意味します。`RETESTITEMS_TIMEOUT_PROFILE_WAIT` 環境変数を使用して設定することもできます。トリガーされたプロファイルに関する詳細は、[プロファイルのドキュメント](https://docs.julialang.org/en/v1/stdlib/Profile/#Triggered-During-Execution)を参照してください。`worker_init_expr` を使用してワーカーのプロファイル設定を調整できます。
  * `failfast::Bool=false`: `true` の場合、テストアイテムが失敗した後は追加のテストアイテムは実行されません。テストアイテムは、再試行後に合格しない場合に失敗したと見なされます。現在の実装では、失敗したテストアイテムと並行して他のワーカーで実行中のテストアイテムは完了することが許可されていますが、これは将来のバージョンで改善される可能性があります。`RETESTITEMS_FAILFAST` 環境変数を使用して設定することもできます。
  * `testitem_failfast::Bool=failfast`: `true` の場合、テストアイテムはテストの失敗またはエラーが発生した時点で停止します。`RETESTITEMS_TESTITEM_FAILFAST` 環境変数を使用して設定することもできます。デフォルトは `failfast` キーワードに渡された値です。`@testitem` が独自の `failfast` キーワードを設定している場合、それが優先されます。`testitem_failfast` キーワードは Julia v1.9+ でのみ効果があり、以前の Julia バージョンでは無視されます。
