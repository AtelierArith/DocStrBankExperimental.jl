```
setsym_oop(bi::BatchedInterface)
```

`n` 個のインデックスプロバイダー（および対応するシンボル）から構成される [`BatchedInterface`](@ref) が与えられた場合、`n` 個の対応する値プロバイダーと値の配列を受け取り、各要素が対応する値プロバイダーの更新された状態値とパラメータ値からなる 2-タプルである `n`-タプルを返す関数を返します。値プロバイダーは [`state_values`](@ref)、[`parameter_values`](@ref) を実装している必要があります。更新は [`remake_buffer`](@ref) を使用してインプレースで行われます。

返される関数に渡されるすべての値プロバイダーは `is_timeseries(prob) === NotTimeseries()` を満たす必要があります。

`n` 個のインデックスプロバイダーの任意のサブセットが共通のシンボルを共有している場合（`BatchedInterface` に渡されたものの中で）、サブセット内のすべての対応する値プロバイダーは共通のシンボルの値で更新されます。

参照: [`is_timeseries`](@ref)、[`NotTimeseries`](@ref)。
