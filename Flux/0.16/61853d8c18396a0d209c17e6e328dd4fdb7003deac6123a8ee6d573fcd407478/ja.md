```
gpu(m)
```

`m`を現在のGPUデバイスにコピーします（現在のGPUバックエンドを使用）。利用可能なGPUがない場合は、何もしません（ただし、最初の実行時に警告を表示します）。これは、Functors.jlに従って構造体に再帰します。

普通の`Array`に戻すには[`cpu`](@ref)を使用してください。また、要素の型のみを変更するには[`f32`](@ref)および[`f16`](@ref)も参照してください。

この関数は、[`gpu_device`](@ref)の周りの便利さのために定義されており、`gpu_device()(m)`と同等です。`device = gpu_device()`を一度定義し、その後`device(m)`を使用してデータを移動させることを検討してもよいでしょう。

# 例

```julia-repl
julia> m = Dense(rand(2, 3))  # Float64の重み行列で構築
Dense(3 => 2)       # 8パラメータ

julia> typeof(m.weight)
Matrix{Float64} (alias for Array{Float64, 2})

julia> m_gpu = gpu(m)  # 同等にm_gpu = m |> gpuと書くことができる
Dense(3 => 2)       # 8パラメータ

julia> typeof(m_gpu.weight)
CUDA.CuArray{Float32, 2, CUDA.Mem.DeviceBuffer}
```
