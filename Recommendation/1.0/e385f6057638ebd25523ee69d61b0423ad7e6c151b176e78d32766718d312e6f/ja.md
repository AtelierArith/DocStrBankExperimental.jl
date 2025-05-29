```
get_data_home([data_home=nothing]) -> String
```

データセットを含むディレクトリへの絶対パスを返します。ディレクトリが存在しない場合は作成し、`data_home=nothing` は環境変数 `JULIA_RECOMMENDATION_DATA` または `~/julia_recommendation_data` にデフォルト設定されます。

参考: [scikit-learnの類似関数](https://github.com/scikit-learn/scikit-learn/blob/7e1e6d09bcc2eaeba98f7e737aac2ac782f0e5f1/sklearn/datasets/_base.py#L34).
