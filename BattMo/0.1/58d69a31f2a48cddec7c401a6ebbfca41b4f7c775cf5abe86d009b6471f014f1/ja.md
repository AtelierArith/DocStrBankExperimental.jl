```
run_battery(inputparams::AbstractInputParams; hook = nothing)
```

与えられた入力に対してバッテリーをシミュレートします。入力はAbstractInputParamsのインスタンスであることが期待されます。このような入力は、関数[`readBattMoJsonInputFile`](@ref)を使用してjsonファイルから準備することができます。
