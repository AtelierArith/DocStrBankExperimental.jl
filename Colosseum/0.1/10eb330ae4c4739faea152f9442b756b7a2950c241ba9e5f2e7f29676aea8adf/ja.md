特定のオブジェクトのセグメンテーションIDを設定する

詳細については、https://microsoft.github.io/AirSim/image_apis/#segmentation を参照してください

引数:     mesh*name (str) IDを設定するメッシュの名前（正規表現をサポート）     object*id (int) 設定するオブジェクトID、範囲 0-255

```
                    IDのRBG値は https://microsoft.github.io/AirSim/seg_rgbs.txt で確認できます
is_name_regex (bool, optional) メッシュ名が正規表現かどうか
```

戻り値:     bool: メッシュが見つかったかどうか
