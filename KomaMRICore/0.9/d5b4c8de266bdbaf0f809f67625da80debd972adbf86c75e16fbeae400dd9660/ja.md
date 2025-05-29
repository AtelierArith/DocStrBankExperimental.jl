```
gpu(x)
```

'x'をGPUに移動します。この関数が機能するためには、'using AMDGPU / CUDA / Metal / oneAPI'でGPUバックエンドをロードする必要があります。

これは関数や`@functor`でマークされた任意の構造体に対して機能します。

普通の`Array`に戻すには[`cpu`](@ref)を使用してください。

要素の型のみを変更するには、[`f32`](@ref)および[`f64`](@ref)も参照してください。

# 例

```julia
using CUDA
x = x |> gpu
```
