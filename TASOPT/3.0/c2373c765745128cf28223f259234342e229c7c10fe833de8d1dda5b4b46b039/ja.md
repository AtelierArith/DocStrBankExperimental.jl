```
stickfig(ac::aircraft; plot_obj = nothing, label_fs = 16, 
        annotate_text = true, annotate_length = true, 
        annotate_group = true, show_grid = false)
```

`stickfig` は、提供された場合はプロットまたはサブプロットオブジェクト `plot_obj` に「スティックフィギュア」飛行機をプロットします（そうでない場合は新しいプロットが作成されます）。これは、最適化の進捗を追跡したり、結果を提示するための要約プロットを作成するために、[`plot_details`](@ref) のような他の関数と組み合わせて使用されます。
