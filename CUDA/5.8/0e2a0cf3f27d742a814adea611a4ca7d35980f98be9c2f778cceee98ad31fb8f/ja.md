```
CuIterator([to], batches)
```

提供された `batches` を `iterate` で反復処理する `CuIterator` を作成します。各反復の際に、現在の `batch` がGPUにコピーされ、前の反復がGPUメモリから解放可能としてマークされます（`unsafe_free!` を介して）。

GPUメモリへの変換は再帰的に行われ、Adapt.jlを使用しているため、各バッチは配列、配列の配列、またはより複雑な反復可能オブジェクトであることができます。変換をカスタマイズするために、最初の引数としてアダプタを指定することができます。たとえば、要素の型を変更するために：

```julia
julia> first(CuIterator([[1.]]))
1-element CuArray{Float64, 1, CUDA.DeviceMemory}:
 1.0

julia> first(CuIterator(CuArray{Float32}, [[1.]]))
1-element CuArray{Float32, 1, CUDA.DeviceMemory}:
 1.0
```

この抽象化は、古い反復が `CuArray` の内部ポーリングメカニズムを介してそれ以外の方法よりも早く解放（または再利用可能としてマーク）される可能性を持つ方法で、データをGPUメモリにバッチ処理するのに役立ちます。
