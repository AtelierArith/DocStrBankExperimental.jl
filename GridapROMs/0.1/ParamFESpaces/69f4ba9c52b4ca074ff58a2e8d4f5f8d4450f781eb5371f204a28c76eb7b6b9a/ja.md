```
parameterize(a::SparseMatrixAssembler,r::AbstractRealization) -> SparseMatrixAssembler
```

`r`のパラメトリック長も保存するアセンブラを返します。この関数は、パラメトリック残差とヤコビ行列を組み立てるために使用されます。アセンブリルーチンは、[`Gridap`](@ref)と同じパイプラインに従います。
