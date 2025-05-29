```
export_model(model::EoSModel,name="";location=".")
```

モデルパラメータをCSVにエクスポートします。`name`キーワード引数が指定されていない場合、ファイルの名前は`singledata_EoS`、`pairdata_EoS`、および`assocdata_EoS`の規則に従います。`location`引数が指定されていない限り、ファイルは現在のディレクトリに保存されます。

すべてのサブモデルパラメータ（例：立方体EoSのアルファ関数パラメータ）もエクスポートされることに注意してください。
