```
plan_implicit_diffusion!(a::Real,dims::Tuple,[fftw_flags=FFTW.ESTIMATE][,nthreads=length(Sys.cpu_info())])
```

[`plan_implicit_diffusion`](@ref)と同様ですが、結果の演算子はデータに対してインプレース操作を実行します。スレッド数`threads`は、システム上の論理CPUコアの数がデフォルトとなります。
