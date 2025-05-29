```
CUDAChaChaStream <: AbstractChaChaStream
```

`CUDAChaChaStream` は、GPU CRNG 用の CUDA 互換の ChaCha キーストリームジェネレーターです。

## 例

ランダム化されたキーを持つ `CUDAChaChaStream` を作成し、それを使っていくつかのランダムな数をサンプリングします：

```julia
julia> rng = CUDAChaChaStream();

julia> x = CuVector{Float32}(undef, 2^10);
```

参照: [`ChaChaStream`](@ref)
