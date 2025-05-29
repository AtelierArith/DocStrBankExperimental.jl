```
addCDSAPIkey(
    key :: AbstractString;
    url :: AbstractString = "https://cds.climate.copernicus.eu/api/v2",
    filename  :: AbstractString = ".cdsapirc",
    overwrite :: Bool = false
) -> nothing
```

ユーザーのCDSAPIキーを`homedir()`内のファイルに追加します（デフォルトでは`.cdsapirc`として指定されています）

## 引数

  * `key` : ユーザーのCDSAPIキー

## キーワード引数

  * `url` : ユーザーのCDSAPIキー
  * `filename`  : URLとキーが`homedir()`内に保存されるファイルの名前
  * `overwrite` : `true`の場合、かつ`filename`がすでに存在する場合は上書きします
