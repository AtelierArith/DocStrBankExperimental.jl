既存のカバレッジデータからカバレッジサマリーを出力します。

```julia
show_coverage(paths=["./src", "./ext"]; root=pwd(), sort_by=nothing)
```

は、`paths`内の追跡されたファイル、ファイル内の追跡された行の総数（"Total"）、カバレッジのある行の数（"Hit"）、カバレッジのない行の数（"Missed"）、およびパーセンテージとしての"Coverage"を示すテーブルを出力します。

カバレッジデータは、`paths`内の`.cov`ファイルおよび`root`内の`tracefile-*.info`ファイルから収集されます。

オプションで、`sort_by`に列の名前を渡すことでテーブルをソートできます。例えば、`sort_py=:Missed`のように。
