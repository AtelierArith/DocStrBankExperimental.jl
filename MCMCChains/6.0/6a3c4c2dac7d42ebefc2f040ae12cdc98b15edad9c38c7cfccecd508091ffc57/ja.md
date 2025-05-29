```
get_params(c::Chains; flatten=false)
```

すべてのパラメータを `NamedTuple` としてパッケージ化して返します。名前にブラケットが含まれる変数（例えば "P[1]"）は、返される値として P にグループ化されます。

`flatten=true` を渡すと、キーがグループ化されていない `NamedTuple` が返されます。

# 例

```jldoctest
julia> chn = Chains(1:5);

julia> x = get_params(chn);

julia> x.param_1
2次元の AxisArray{Int64,2,...} で、軸は次のようになります:
    :iter, 1:1:5
    :chain, 1:1
データは、5×1 の行列 {Int64}:
 1
 2
 3
 4
 5
```
