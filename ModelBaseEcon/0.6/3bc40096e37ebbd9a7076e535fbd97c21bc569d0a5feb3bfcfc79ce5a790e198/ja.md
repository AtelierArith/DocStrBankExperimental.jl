```
export_model(model, name, file::IO)
export_model(model, name, path::String)
```

モデルをモジュールファイルにエクスポートします。`name`パラメータはモジュールの名前とモジュールファイルの名前に使用されます。モジュールファイルは、オプションの第三引数で指定されたディレクトリに作成されます。
