```
nvmon(f, group_or_groups[; gpuids])
```

指定された関数 `f` を1つまたは複数のGPUで実行しながらパフォーマンスグループを監視します。注意点：

  * `NvMon.init` と `NvMon.finalize` は自動的に呼び出されます
  * 複数のパフォーマンスグループの測定は逐次的であり、`f` の複数回の実行が必要です！

**キーワード引数：**

  * `gpuids` (デフォルト: 最初のGPU): 監視するGPUを指定します

**注意: これは実験的な機能であり、いつでも変更または削除される可能性があります！**

# 例

```julia
julia> using LIKWID

julia> x = CUDA.rand(1000); y = CUDA.rand(1000);

julia> metrics, events = nvmon("FLOPS_DP") do
           CUDA.@sync x .+ y;
       end;
```
