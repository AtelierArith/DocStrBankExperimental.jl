```
KeplerGLMap(token::String;
    width::Int64 = 1200,
    height::Int64 = 900,
    center_map = true,
    read_only = false,
    config = KeplerGLBase.make_static_config())
```

新しい `KeplerGLMap` を作成します。

# 必須引数

  * `token::String`: マップを表示するために使用されるマップボックストークン。

# オプション引数

  * `width:Int64 = 1200`: マップウィンドウの幅
  * `height:Int64 = 900`: マップウィンドウの高さ
  * `center_map - true`: マップが自動的に中央に配置されるべきかどうか
  * `read_only = false`: マップが読み取り専用（編集不可）であるべきかどうか
  * `config = KeplerGLBase.make_static_config()`: 初期設定
