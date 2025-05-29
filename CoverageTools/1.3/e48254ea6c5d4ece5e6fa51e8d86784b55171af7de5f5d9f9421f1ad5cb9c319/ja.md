```
amend_coverage_from_src!(coverage::Vector{CovCount}, srcname)
amend_coverage_from_src!(fc::FileCoverage)
```

Juliaのコードカバレッジ機能は、コンパイルされた行のみを報告します。未使用の関数（または破棄された行）は、したがって、誤って`nothing`として記録される可能性がありますが、代わりに0であるべきです。この関数は、既存の結果を取り込み、関数内にある可能性のあるソース行をマークするためにカバレッジベクターをインプレースで更新します。
