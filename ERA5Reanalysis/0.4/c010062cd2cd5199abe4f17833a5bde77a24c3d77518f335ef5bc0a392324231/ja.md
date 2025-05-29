```
PressureVariable(
    ID :: AbstractString,
    ST = String;
    hPa   :: Int = 0
    throw :: Bool = true
) -> evar :: SingleLevel
```

`ID`で定義された圧力レベル変数の基本的なプロパティを取得し、`hPa`で示される圧力高さにおいて、`evar` SingleLevel型構造体に格納します。

# 引数

  * `ID` : NetCDFファイルで使用される変数ID（文字列形式）

# キーワード引数

  * `hPa` : hPaで指定された圧力レベルの高さを示す整数
  * `throw` : `hPa`レベルが存在しない場合、`throw`がtrueであればエラーをスローし、そうでなければ最も近い圧力レベルを見つけます。
