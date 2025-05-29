```
apply_operator!(working_memory, target, source, operator, boost=1, compress=Val(true)) ->
    stat_names, stats, working_memory, target
```

単一の行列(/演算子)-ベクトルの乗算を実行します：

$$
v^{(n + 1)} = \hat{T} v^{(n)} ,
$$

ここで、$\hat{T}$は`operator`、$v^{(n+1)}$は`target`、$v^{(n)}$は`source`です。`working_memory`は一時的なストレージとして使用できます。

`boost`引数は[`apply_column!`](@ref)に渡され、実行されるスパーンの数を増加させます。ベクトルを圧縮せずに演算子を適用するには、`compress`を`Val(false)`に設定します。

操作が確率的、半確率的、または決定論的に行われるかどうかは、トレイト`StochasticStyle(target)`によって制御されます。[`StochasticStyle`](@ref)を参照してください。

`StochasticStyle`によって生成されたステップ統計、作業メモリ、および`target`ベクトルを返します。`target`と`working_memory`は変更および/または入れ替えられる場合があります。
