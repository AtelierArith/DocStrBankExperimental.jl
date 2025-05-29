```
getsym(bi::BatchedInterface)
```

`n` 個のインデックスプロバイダー（および対応するシンボル）から構成される [`BatchedInterface`](@ref) が与えられた場合、`n` 個の対応する値プロバイダーを受け取り、ユニオン内のシンボルの値の配列を返す関数を返します。返された関数には、適切な `eltype` とサイズの `AbstractArray` を最初の引数として渡すこともでき、その場合、操作はユニオン内のシンボルの値で配列をインプレースで埋めます。

`getsym` によって返された関数に渡されるすべての値プロバイダーは、`is_timeseries(prob) === NotTimeseries()` を満たす必要があります。

ユニオン内の `i` 番目のシンボルの値（`variable_symbols(bi)[i]` を通じて取得）は、関連するインデックスプロバイダーに対応する問題から取得されます（つまり、`associated_systems(bi)[i]` のインデックスにある値プロバイダーから）。

参照: [`variable_symbols`](@ref), [`associated_systems`](@ref), [`is_timeseries`](@ref), [`NotTimeseries`](@ref).
