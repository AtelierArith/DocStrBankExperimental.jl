```
state_values(valp)
state_values(valp, i)
```

値プロバイダー `p` のすべての状態の値を含むインデックス可能なコレクションを返します。`is_timeseries(valp)` が [`Timeseries`](@ref) の場合、対応するタイムステップでの状態値を含む配列のベクトルを返します。この場合、2引数バージョンの関数も、タイムステップ `i` での状態値を効率的に返すように実装できます。デフォルトでは、2引数メソッドは `state_values(valp)[i]` を呼び出します。`i` が複数のインデックス（例えば、`Colon`、`AbstractArray{Int}`、`AbstractArray{Bool}`）で構成されている場合、効率のために特化したメソッドが定義されることがあります。デフォルトでは、`state_values(valp, ::Colon) = state_values(valp)` で、タイムシリーズのコピーを避けます。

この関数が `AbstractArray` で呼び出されると、同じ配列が返されます。

参照: [`is_timeseries`](@ref)
