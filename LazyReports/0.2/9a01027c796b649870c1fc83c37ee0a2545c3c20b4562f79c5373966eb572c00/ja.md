```
lazyreport!(rpt::LazyReport, contents...)
```

レポート `rpt` にさらにコンテンツを追加します。例については [`lazyreport`](@ref) を参照してください。

# 実装

`lazyreport!(rpt::LazyReport, obj::MyType)` を直接特化しないでください。代わりに、低レベルの関数 [`LazyReports.pushcontent!`](@ref) を特化してください。
