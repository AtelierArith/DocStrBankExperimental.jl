```julia
GMM_dataset(k, d, n; center, out_dic, kwargs...)

```

`n` 列を持つデータセット X を返します。これらの列は `k` 個のガウス分布の混合に従って生成されます。生成プロセスに関する追加情報は、辞書 `out_dic` を渡すことで得られます。キーワード引数が渡される [`random_GMM`](@ref) も参照してください。
