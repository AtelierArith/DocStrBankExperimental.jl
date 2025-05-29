```
write_parameters(parameters, url::String; <keyword arguments>)
```

`parameters`を指定されたRFC-1738 `url`のSpineデータベースに書き込みます。`parameters`は、パラメータ名を別の辞書にマッピングし、オブジェクトまたはリレーションシップ（`NamedTuple`）を値にマッピングする辞書です。

# 引数

  * `parameters::Dict`: パラメータ名をエンティティに、パラメータ値にマッピングする辞書
  * `upgrade::Bool=true`: `url`のデータベースを最新のリビジョンにアップグレードするかどうか。
  * `for_object::Bool=true`: 次元数が1の場合にオブジェクトパラメータまたは1Dリレーションシップパラメータを書き込むかどうか。
  * `report::String=""`: 書き込まれるパラメータに追加される余分な次元として追加されるレポートオブジェクトの名前。
  * `alternative::String`: パラメータ値を書き込む代替先。
  * `comment::String=""`: 書き込み操作の性質を説明するコメント。
