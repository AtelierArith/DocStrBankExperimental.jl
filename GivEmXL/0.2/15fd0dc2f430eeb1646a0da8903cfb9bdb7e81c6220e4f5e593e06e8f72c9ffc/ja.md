```
proc_n_save(procwhole_fn, procsubset_fn, postproc_fn;
    xlfile,
    datafiles=nothing, 
    paramsets = [(;)],
    ) → (; overview, subsets_results, résumé, errors, dfs)
```

ユーザーが提供した関数を使用してデータを処理するために [`proc_data`](@ref) を呼び出し、その後 [`save_results`](@ref) を呼び出します。 引数と返される値の説明については、これらの関数のドキュメントを参照してください。

関数 `proc_n_save` はエクスポートされています。
