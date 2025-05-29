```
abstract type Proj_NEP <: NEP
```

`Proj_NEP`は投影された`NEP`を表します。投影は次のように定義されます。

$$
N(λ)=W^HM(λ)V
$$

ここで、$M(λ)$は基底NEPであり、`W`と`V`は投影空間の基底を表す矩形行列です。インスタンスは`create_proj_NEP`を使用して作成されます。例については[`create_proj_NEP`](@ref)を参照してください。

任意の`Proj_NEP`は、投影を操作するために2つの関数を実装する必要があります。

  * [`set_projectmatrices!`](@ref): 行列`W`と`V`を設定します。
  * [`expand_projectmatrices!`](@ref): 行列`W`と`V`を1列拡張します。
