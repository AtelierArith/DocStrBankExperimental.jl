```
recover_nearest(code, latitude, longitude)
```

指定された場所に最も近い一致するコードを回復します。4文字から7文字の短いコードを指定すると、指定された場所に最も近い一致するフルコードを回復します。

# 引数:

  * `code`: 有効なOLC文字列。
  * `latitude`: 最も近い一致するフルコードを見つけるために使用する緯度（符号付き度）。
  * `longitude`: 最も近い一致するフルコードを見つけるために使用する経度（符号付き度）。

# 戻り値:

短いコードに一致する参照位置に最も近いフルオープンロケーションコード。渡されたコードが有効な短いコードでなかった場合でも、有効なフルコードであれば、適切な大文字小文字で返されますが、それ以外は変更されません。
