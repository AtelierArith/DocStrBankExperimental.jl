```
@testset "スイート名" begin ... end
@testset [before_each=()->...] [after_each=()->...] [metrics=DefaultTestMetrics]
           [success_handler=(testset)->...] [failure_handler=(testset)->...]
           [xml_report=false] [html_report=false] "スイート名" begin ... end
```

テストスイートをスケジュールします

`@testset` と `@testset` マクロは非常に似ています。唯一の違いは、最上位の `@testset` はテストケースを実行しますが、最上位の `@testset` はその基になるテストケースを実行せず（スケジュールするだけです）、このマクロの結果に対して `run_testset` を明示的に呼び出す必要があります。

また、`@testset` の本体は常にスケジュール時に実行されることに注意してください。これは、可能な基になる `@testcase` を収集する必要があるためです。したがって、テストを `@testset` の下に置くのではなく、`@testcase` の下に置くことが良いプラクティスです。`@testset` の下に定義されたテストは、スケジュール時に逐次的に実行されます。

## キーワード引数

`@testset` は7つの追加パラメータを受け取ります：

  * `before_each`: 各基になるテストケースの前に実行する関数
  * `after_each`: 各基になるテストケースの後に実行する関数
  * `metrics`: カスタム `TestMetrics` タイプ
  * `success_handler`: すべてのテストの成功した処理の後に実行する関数。この関数はテストスイートを引数として受け取ります。この引数は最上位の `@testset` のみで機能します。
  * `failure_handler`: すべてのテストの失敗した処理の後に実行する関数。この関数はテストスイートを引数として受け取ります。この引数は最上位の `@testset` のみで機能します。
  * `xml_report`: 最後にXML出力ファイルを生成するかどうか。この引数は最上位の `@testset` のみで機能します。
  * `html_report`: 最後にHTML出力ファイルを生成するかどうか。この引数は最上位の `@testset` のみで機能します。
