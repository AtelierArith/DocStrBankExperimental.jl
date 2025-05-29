```
flux_ranocha_turbo(u_ll, u_rr, orientation_or_normal_direction, equations)
```

[`flux_ranocha`](@ref) と同等ですが、[`VolumeIntegralFluxDifferencing`](@ref) と一緒に使用される場合など、専門的なメソッドを使用する可能性があります。これらの専門的なメソッドは、最新のハードウェアでの実行時効率を向上させるために、SIMD命令のより良い利用を可能にする場合があります。
