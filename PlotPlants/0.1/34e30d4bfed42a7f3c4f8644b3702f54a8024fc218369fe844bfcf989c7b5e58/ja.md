```
save_gif!(figs::Array, fps::Int, gif::String)
save_gif!(imgs::Array{Array,1}, fps::Int, fn::String)
```

GIFとして図の配列を保存します。次の引数が必要です。

  * `figs` 図の配列
  * `fps` 秒あたりのフレーム数
  * `fn` 保存するGIFのファイル名
  * `imgs` 配列の配列（読み込まれた図）
