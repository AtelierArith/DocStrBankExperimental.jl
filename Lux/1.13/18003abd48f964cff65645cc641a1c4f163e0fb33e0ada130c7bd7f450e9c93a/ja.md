```
FromFluxAdaptor(preserve_ps_st::Bool=false, force_preserve::Bool=false)
```

FluxモデルをLuxモデルに変換します。

!!! warning "`active` フィールド"
    これは、いくつかのFluxレイヤーの`active`フィールドを常に無視します。これはほとんどサポートされることはありません。


## キーワード引数

  * `preserve_ps_st`: レイヤーの状態とパラメータを保持するために`true`に設定します。これは元のモデルを保持するための最善の方法を試みますが、失敗する可能性があります。可能な失敗をオーバーライドする必要がある場合は、`force_preserve`を`true`に設定してください。
  * `force_preserve`: 状態とパラメータの保持を伴う変換のいくつかはまだ実装されていません。この場合、`force_transform`が`false`の場合は警告が表示され、コアLuxレイヤーが返されます。それ以外の場合は、[`FluxLayer`](@ref)が作成されます。

## 例

```julia
julia> import Flux

julia> using Adapt, Lux, Random

julia> m = Flux.Chain(Flux.Dense(2 => 3, relu), Flux.Dense(3 => 2));

julia> m2 = adapt(FromFluxAdaptor(), m); # または FromFluxAdaptor()(m.layers)

julia> x = randn(Float32, 2, 32);

julia> ps, st = Lux.setup(Random.default_rng(), m2);

julia> size(first(m2(x, ps, st)))
(2, 32)
```
