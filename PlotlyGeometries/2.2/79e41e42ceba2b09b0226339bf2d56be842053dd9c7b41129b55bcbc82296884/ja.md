```
polygons(pts::Vector, ng::Int, color::String; opc::Real=1, ah::Real=0)

一連の点と指定された数の頂点からポリゴンのグループを作成します。

# 引数
- `pts::Vector`: メッシュを定義する点のリスト。
- `ng::Int`: ポリゴンごとの頂点の数。
- `color::String`: メッシュの色。

# キーワード
- `opc`: メッシュの不透明度。デフォルトは1。
- `ah`: アルファハル値。
```
