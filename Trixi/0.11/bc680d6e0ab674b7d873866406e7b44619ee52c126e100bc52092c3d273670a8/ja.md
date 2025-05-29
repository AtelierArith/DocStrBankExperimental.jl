```
flux_shima_etal_turbo(u_ll, u_rr, orientation_or_normal_direction, equations)
```

[`flux_shima_etal`](@ref) と同等ですが、[`VolumeIntegralFluxDifferencing`](@ref) などで使用される場合に特化したメソッドを使用する可能性があります。これらの特化したメソッドは、最新のハードウェアでの実行時効率を向上させるために、SIMD命令のより良い利用を可能にする場合があります。
