```
humann_barplot(comm::CommunityProfile, outpath; kwargs...)
```

機能データからプロットを生成するための `humann_barplot` スクリプトのラッパーです。スクリプトオプションのためにキーワード引数を渡してください。フラグ引数は `true` に設定する必要があります。例えば

```julia-repl
julia> humann_barplot(comm, "plot.png"; focal_metadata="STSite", focal_feature="COA-PWY",
                      sort="braycurtis",
                      scaling="logstack",
                      as_genera=true,
                      remove_zeros=true)
```

[`humann`](https://github.com/biobakery/humann) のインストールが必要で、`ENV["PATH"]` に利用可能です。詳細については "[Using Conda](@ref using-conda)" を参照してください。
