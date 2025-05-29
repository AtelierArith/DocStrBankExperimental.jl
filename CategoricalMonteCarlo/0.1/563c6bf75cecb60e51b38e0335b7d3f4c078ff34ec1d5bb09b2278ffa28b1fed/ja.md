```
tsample(::Type{T<:Real}=Int, A::AbstractArray, n_sim::Int; [dims=:], [n_cat=nothing], [chunksize=5000])
```

`sample`の完全なドキュメントを参照してください。動作は同一ですが、スレッドベースの並列処理を使用して計算を加速します。

オプションの`chunksize`引数は、各スレッドに渡されるシミュレーションの数の固定上限を提供します。サンプルを取得する独立したカテゴリ分布の数と実行されるシミュレーションの数に応じて、`chunksize`が`5000`はおそらく保守的すぎます。ユーザーはより小さなチャンクサイズを試すことをお勧めします。

また、[`sample`](@ref)、[`vsample`](@ref)、[`vtsample`](@ref)も参照してください。
