```
polygons(pts::Vector, color::String; opc::Real=1, ah::Real=0)

一連の点からポリゴンメッシュを作成します（点のセットの中点の周りに形成されます）。

# 引数
- `pts::::Vector`: ポリゴンを定義する点のリスト。
- `color::String`: ポリゴンの色。

# キーワード
- `opc`: ポリゴンの不透明度。デフォルトは1。
- `ah`: アルファハル値。デフォルトは0。
```
