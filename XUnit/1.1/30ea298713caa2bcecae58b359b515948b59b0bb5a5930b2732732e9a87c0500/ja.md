```
@testcase "テストケース名" begin ... end
@testcase [before_each=()->...] [after_each=()->...] [metrics=DefaultTestMetrics]
          [success_handler=(testcase)->...] [failure_handler=(testcase)->...]
          [xml_report=false] [html_report=false] "テストケース" begin ... end
```

自己完結型のテストケースを定義します。

テストケースはスケジューリング時に集められ、テストランナーを使用して実行されます。テストランナーはテストを任意の順序で（さらには複数のスレッド/プロセスで）実行できるため、テストケースが互いに依存しないことを強く推奨します。

## キーワード引数

`@testcase` は4つの追加パラメータを受け取ります：

  * `metrics`: カスタム `TestMetrics` タイプ
  * `success_handler`: すべてのテストが成功裏に処理された後に実行される関数。この関数はテストスイートを引数として受け取ります。この引数は最上位の `@testcase` のみで機能します。
  * `failure_handler`: すべてのテストが失敗した後に実行される関数。この関数はテストスイートを引数として受け取ります。この引数は最上位の `@testcase` のみで機能します。
  * `xml_report`: 最後にXML出力ファイルを生成するかどうか。この引数は最上位の `@testcase` のみで機能します。
  * `html_report`: 最後にHTML出力ファイルを生成するかどうか。この引数は最上位の `@testcase` のみで機能します。
