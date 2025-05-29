# TestFunctionRunner

パッケージ内でテストを定義するためのややハッキーな解決策です。特に、このパッケージは以下のような厄介な詳細を処理します：

  * doctest（または任意の `eval` ベースのテスト）
  * Distributed.jl のテストコードを読み込む必要があるテスト

このパッケージは、テストの*定義*とテストの*実行*フェーズの明確な分離を目指しています。

## クイックスタート

`Pkg.test` 互換のテストエントリポイント `test/runtests.jl` を作成するには：

1. `test/$TestPackageName/` にパッケージを作成します（すなわち、`test/$TestPackageName/Project.toml` と `test/$TestPackageName/src/$TestPackageName.jl` が存在します）。
2. 引数を取らず、名前が `test_` で始まる関数としてテストを書く。結果を主張するために、通常通り `Test.@test` などを使用します。
3. 次のコードで `test/runtests.jl` を作成します：

    `julia  using TestFunctionRunner  TestFunctionRunner.@run`

**注意:** テスト依存関係は、`test/Project.toml` と `test/$TestPackageName/Project.toml` の両方にリストされている必要があります。

テストパッケージまたはそのサブモジュールは、`TestFunctionRunner.run(module)` を使用して実行することもできます。

## テストの定義

以下のフック/コールバックは*テストモジュール*で定義できます。すなわち、名前が `Test` で始まり、その後に大文字が続くモジュールです。

### `test()`

### `test_*()`

関数がテストを定義する場合：

  * 名前が `test` であるか、名前が `test_` で始まり、
  * 引数を取らない

### `module_context(f)`

`module_context` という名前の関数はモジュールコンテキストを定義します。モジュール全体とサブモジュールのセットアップとティアダウンを定義するために使用できます：

```JULIA
function module_context(f)
   setup()
   try
      f()
   finally
      teardown()
   end
end
```

ここで `f` は、このモジュールとそのサブモジュールのテスト関数を実行する関数です。

### 実験的

#### `timeout_of(test_function)`

`timeout_of` という名前の関数は、各テスト関数のタイムアウト（秒単位）をカスタマイズするために使用できます。`nothing` を返すことは、グローバル設定にフォールバックすることを意味します。

#### `should_test_module()`

`should_test_module` という名前の関数が存在し、`false` を返す場合、モジュールおよびサブモジュール内のすべてのテストはテストされません。

#### `before_test_module()`

`before_test_module` という名前の関数が存在する場合、このモジュール内でテストを実行する前に呼び出されます。

#### `after_test_module()`

`after_test_module` という名前の関数が存在する場合、このモジュール内でテストを実行した後に呼び出されます。

## テストの実行

### 一般的なオプション

`TestFunctionRunner.@run` と `TestFunctionRunner.run` は以下のオプションをサポートします：

#### `$TEST_FUNCTION_RUNNER_JL_TIMEOUT`

#### `timeout`

**各**テスト関数のタイムアウト（秒単位）。関数が指定された制限を超えて時間がかかる場合、テストを実行している**全体の `julia` プロセス**が終了します。TestFunctionRunner.jl は可能であればスタックトレースを印刷しようとします。

注意：これはUnixシステムでのみ機能します。

環境変数 `TEST_FUNCTION_RUNNER_JL_TIMEOUT` は、`timeout` のデフォルト値を設定するために使用できます。関数およびマクロの引数は環境変数をオーバーライドします。

#### `$TEST_FUNCTION_RUNNER_JL_FASTFAIL`

#### `failfast`

`true` の場合、最初の失敗時にテストの実行を停止します。

環境変数 `TEST_FUNCTION_RUNNER_JL_FASTFAIL` は、`failfast` のデフォルト値を設定するために使用できます。関数およびマクロの引数は環境変数をオーバーライドします。値 `true`、`yes` および `1`（大文字小文字を区別しない）は `true` として扱われます。

### `@run` オプション

#### `paths`

追加のロードパス。相対パスは現在のファイルの親ディレクトリに対して解決されます。例：`TestFunctionRunner.@run(paths = ["../benchmark/MyBenchmarks/"])`。

#### `packages`

相対ファイルパスによってテストされるパッケージを指定します。すなわち、`Project.toml` または `JuliaProject.toml` を含むディレクトリです。`@__DIR__/$TestPackage/src/$TestPackage.jl` にあるパッケージは、指定されていない場合にテストされます。
