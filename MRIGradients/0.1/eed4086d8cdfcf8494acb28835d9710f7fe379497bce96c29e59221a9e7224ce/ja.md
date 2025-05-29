```
readGIRFFile(g::GirfEssential, pathX::String, pathY::String, pathZ::String, varName::String, doFilter::Bool)
```

特定の変数名を持つGIRFファイルを読み込み、対応するGIRFEssentialオブジェクトを返す関数です。

# 引数

  * `pathX::String` - X軸のGIRF MATファイルのフルパス
  * `pathY::String` - Y軸のGIRF MATファイルのフルパス
  * `pathZ::String` - Z軸のGIRF MATファイルのフルパス
  * `varName::String` - MATファイルからGIRFデータとして読み込む必要がある変数名。
  * `doFilter::Bool` - Tukeyフィルターを使用してGIRFデータをフィルタリングするかどうか

# 出力

  * g::GirfEssential - 読み込まれたデータを持つ構築されたGirfEssentialオブジェクト。
