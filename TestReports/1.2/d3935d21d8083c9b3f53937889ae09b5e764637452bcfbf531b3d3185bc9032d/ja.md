```
report(ts::AbstractTestSet) -> XMLDocument
```

含まれている `TestSet` と `Result` に関する JUnit XML レポートを生成します。JUnit XML スキーマはネストされた `testsuite` 要素を許可していないため、レポートは階層的な `TestSet` 構造をフラット化します。各 `TestSet` は `testsuite` 要素になり、各 `Result` は `testcase` 要素になります。

`Result` は親 `TestSet` 内で一度だけ報告され、レポート内での重複エントリを避け、合計テスト数が Julia の出力と一致しない問題を回避します。

`ts` に含まれるすべての `AbstractTestSet` は `description::AbstractString` フィールドと反復可能な `results` フィールドを持っている必要があります。
