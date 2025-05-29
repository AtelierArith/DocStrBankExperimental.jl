```
test_file(file::AbstractString; jetconfigs...)
```

[`report_file`](@ref)を実行し、問題が検出されないことをテストします。

[`report_file`](@ref)と同様に、[一般的な設定](@ref)および[エラー分析特有の設定](@ref jetanalysis-config)をオプション引数として指定できます。

[`@test_call`](@ref)と同様に、`test_file`は[`Test`標準ライブラリ](https://docs.julialang.org/en/v1/stdlib/Test/)と完全に統合されています。詳細については[`@test_call`](@ref)を参照してください。
