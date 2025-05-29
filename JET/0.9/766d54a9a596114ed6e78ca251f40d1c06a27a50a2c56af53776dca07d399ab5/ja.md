```
test_package(package::Module; jetconfigs...)
test_package(package::AbstractString; jetconfigs...)
test_package(; jetconfigs...)
```

[`report_package`](@ref)を実行し、問題が検出されないことをテストします。

[`report_package`](@ref)と同様に、[一般的な設定](@ref)および[エラー分析特有の設定](@ref jetanalysis-config)をオプション引数として指定できます。

[`@test_call`](@ref)と同様に、`test_package`は[`Test`標準ライブラリ](https://docs.julialang.org/en/v1/stdlib/Test/)と完全に統合されています。詳細については[`@test_call`](@ref)を参照してください。

```julia
julia> @testset "test_package" begin
           test_package("Example"; toplevel_logger=nothing)
       end;
Test Summary: | Pass  Total  Time
test_package  |    1      1  0.0s
```
