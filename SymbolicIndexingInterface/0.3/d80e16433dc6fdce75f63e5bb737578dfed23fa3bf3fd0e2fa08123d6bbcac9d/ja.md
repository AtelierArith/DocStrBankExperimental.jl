```
setsym(bi::BatchedInterface)
```

`n` 個のインデックスプロバイダー（および対応するシンボル）から構成される [`BatchedInterface`](@ref) が与えられた場合、`n` 個の対応する問題と値の配列を受け取り、各問題を対応するシンボルの値で更新する関数を返します。

`setsym` によって返される関数に渡されるすべての値プロバイダーは、`is_timeseries(prob) === NotTimeseries()` を満たす必要があります。

`n` 個のインデックスプロバイダーのいずれかのサブセットが共通のシンボルを共有している場合（`BatchedInterface` に渡されたものの中で）、そのサブセット内のすべての対応する値プロバイダーは共通のシンボルの値で更新されます。

参照: [`is_timeseries`](@ref), [`NotTimeseries`](@ref).
