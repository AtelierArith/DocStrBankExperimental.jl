```
save_neural_model(file, model, options)
```

`file`、`model`、および `optimize` によって生成された `options` を指定して、すべてを `.MAT` ファイルに保存します。この方法で `reload_neural_data` がこれらのものを Julia ワークスペースに戻すことができるか、MATLAB に読み込むことができます。

関連情報: [`reload_neural_model`](@ref)
