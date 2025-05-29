```
@ps_show(...)
```

`Base.@show`に類似したマクロを呼び出します。これは、[`@init_parallel_stencil`](@ref)で選択された並列化用のパッケージと互換性があります（ThreadsまたはPolyesterの場合はBase.@show、CUDAの場合はCUDA.@cushow）。
