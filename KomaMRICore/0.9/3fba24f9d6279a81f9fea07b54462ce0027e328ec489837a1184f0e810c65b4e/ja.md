```
gpu(x, backend)
```

'backend' パラメータで指定された GPU バックエンドに `x` を移動しようとします。

これは関数や `@functor` でマークされた任意の構造体に対して機能します。

普通の `Array` に戻すには [`cpu`](@ref) を使用してください。

要素の型のみを変更するには、[`f32`](@ref) および [`f64`](@ref) も参照してください。

# 例

```julia
x = gpu(x, CUDABackend())
```
