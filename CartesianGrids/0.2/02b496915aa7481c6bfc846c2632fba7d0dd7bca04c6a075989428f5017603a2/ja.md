```
plan_intfact!(a::Real,dims::Tuple,[fftw_flags=FFTW.ESTIMATE][,nthreads=length(Sys.cpu_info())])
```

[`plan_intfact`](@ref) と同様ですが、結果のオペレーターはデータに対してインプレース操作を行います。スレッド数 `threads` は、システム上の論理CPUコアの数にデフォルト設定されています。
