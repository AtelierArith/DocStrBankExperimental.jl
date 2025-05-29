```
FileIO.load(file, ::Type{<:UnfoldModel}; generate_Xs=true)
```

.jld2ファイルからUnfoldModelをロードします。

デフォルトでは、デザインマトリックスが再構築されます。必要ない場合は`generate_Xs=false`に設定すると、時間効率が向上します。
