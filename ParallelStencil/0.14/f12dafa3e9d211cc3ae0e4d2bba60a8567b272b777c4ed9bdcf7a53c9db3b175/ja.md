```
@ps_println(...)
```

`Base.@println`に類似したマクロを呼び出し、[`@init_parallel_stencil`](@ref)で選択された並列化用のパッケージと互換性があります（ThreadsまたはPolyesterの場合はBase.@println、CUDAの場合はCUDA.@cuprintln）。
