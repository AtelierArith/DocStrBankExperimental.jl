```
@kwdef struct Contract
    is_relaxed::Bool = false
    axes::Maybe{ContractAxes} = nothing
    data::Maybe{ContractData} = nothing
end
```

計算ツールの契約で、`axes` と `data` を指定します。`is_relaxed` が true の場合、追加の入力および/または出力を許可します。これは通常、計算にクエリパラメータがあり、その追加データにアクセスする必要がある場合や、計算が可変のデータセットを生成する場合に使用されます。

!!! note
    関数がいくつかの関数を連続して呼び出す場合、[`function_contract`](@ref DataAxesFormats.Computations.function_contract) を使用してその契約を計算し、次に呼び出し順に結果を `|>` を使って組み合わせることができます。

