```
ReportingTestSet
```

`TestReports.jl`によってJUnit XMLの作成に使用されるカスタム`AbstractTestSet`タイプです。

テストが失敗したりエラーが発生した場合にエラーをスローしません。`finish`時に、`ReportingTestSet`はデフォルトのテスト出力を表示し、その後レポート生成に適した構造にフラット化します。

これはパッケージの`runtests.jl`ファイルの周りにラップされるように設計されており、テスト結果が表示されるときと`TestSet`が`finish`時にフラット化されるときにこれが前提とされています。使用例については`bin/reporttests.jl`を参照してください。`ReportingTestSet`はパッケージのテストで直接使用することを意図しておらず、これは推奨されずサポートされていません。

`ReportingTestSet`は`DefaultTestSet`に従って`description`および`results`フィールドを持ち、以下の追加フィールドがあります：

  * `testset_properties`: レポートに挿入するためのテストセットプロパティを記録するために使用されます。
  * `test_properties`: レポートに挿入するためのテストプロパティを記録するために使用されます。
  * `start_time::DateTime`: テストの開始日時（ローカルシステム時間）。
  * `time_taken::Millisecond`: `TestSet`を実行するのにかかった時間（ミリ秒）。
  * `last_record_time::DateTime`: `record`が最後に呼び出された時間。
  * `hostname::String`: テストセットが実行されたホストの名前。

また、[`flatten_results!`](@ref)、[`record_testset_property`](@ref)、[`record_testset_property`](@ref)、および[`report`](@ref)も参照してください。
