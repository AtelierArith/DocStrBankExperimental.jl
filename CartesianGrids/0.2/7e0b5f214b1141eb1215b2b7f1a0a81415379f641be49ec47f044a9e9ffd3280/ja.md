```
plan_laplacian!(dims::Tuple,[with_inverse=false],[fftw_flags=FFTW.ESTIMATE],
                      [factor=1.0][,nthreads=length(Sys.cpu_info())])
```

[`plan_laplacian`](@ref)と同様ですが、データに対してインプレースで操作します。スレッド数`threads`は、システム上の論理CPUコアの数がデフォルトです。
