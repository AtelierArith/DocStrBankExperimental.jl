```
groupby(f, t, by = pkeynames(t); select, flatten=false, usekey = false)
```

`f`を`by`のユニークな値で定義されたグループ内の`select`された列に適用します（[`select`](@ref)を参照）。

`f`がベクトルを返す場合、`flatten = true`を使用して複数の列に分割します。

結果のグループにグルーピングキーを保持するには、`usekey = true`を使用します。

# 例

```
using Statistics

t=table([1,1,1,2,2,2], [1,1,2,2,1,1], [1,2,3,4,5,6], names=[:x,:y,:z])

groupby(mean, t, :x, select=:z)
groupby(identity, t, (:x, :y), select=:z)
groupby(mean, t, (:x, :y), select=:z)

groupby((mean, std, var), t, :y, select=:z)
groupby((q25=z->quantile(z, 0.25), q50=median, q75=z->quantile(z, 0.75)), t, :y, select=:z)

# 異なる列に異なる集約関数を適用
groupby((ymean = :y => mean, zmean = :z => mean), t, :x)

# グルーピングキーを含める
groupby(t, by; usekey = true) do key, dd
    # keyをキー（名前付きタプル）として、ddをデータとして使用するコード
end
```
