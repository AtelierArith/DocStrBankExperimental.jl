```
mk_gif(data, title="", xlabel="時間, t", 
             ylabel="出力, y(t)",
             savename="応答")
```

プロセス応答の .gif を作成します。`data` は、[`simulate`](@ref) から返される可能性のある `:t` と `:output` の2列を持つデータフレームです。[`viz_response`](@ref) と同じ引数を受け入れます。.gif を作成するには ImageMagick をインストールする必要があります。.gif はファイル `savename` として保存されます。

# 引数

  * `data::DataFrame`: 時系列データのデータフレームで、時間のための `:t` 列と出力のための `:output` 列を含みます。
  * `title::String`: プロットのタイトル
  * `xlabel::String`: xラベル
  * `ylabel::String`: yラベル
  * `savename::String`: .gif として保存するファイル名。提供されていない場合は .gif 拡張子が自動的に追加されます。
