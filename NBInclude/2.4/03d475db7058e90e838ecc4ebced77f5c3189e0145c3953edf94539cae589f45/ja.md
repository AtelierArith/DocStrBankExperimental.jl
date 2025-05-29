```
nbexport(io, nbpath; regex=r"", markdown=true)
nbexport(output_filename, nbpath; regex=r"", markdown=true)
```

IJulia Jupyterノートブックファイル`nbpath`を読み込み、`io`ストリームまたは`output_filename`ファイルに通常のJuliaコードとして出力します。

ノートブック内のMarkdownセルは解析され、`# ...`コメントに変換されます。ただし、`markdown`キーワード引数が`false`に設定されている場合（この場合、Markdownセルは無視されます）。

`@nbinclude`と同様に、`regex`キーワードを介して渡された正規表現に一致しないコードセルは無視されます。
