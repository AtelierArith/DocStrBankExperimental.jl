```
visualize(coord_logger, boundary, out_filepath; <keyword arguments>)
```

シミュレーションをアニメーションとして視覚化します。

この関数はGLMakieがインポートされているときのみ利用可能です。シミュレーションの長さや原子の数によって、実行に時間がかかる場合があります。

# 引数

  * `connections=Tuple{Int, Int}[]`: 結合する原子のインデックスのペア。
  * `connection_frames`: 結合が表示されるフレーム。フレームの数と同じ長さのリストで、各アイテムは`connections`と同じ長さの`Bool`のリストである必要があります。デフォルトでは常に`true`です。
  * `trails::Integer=0`: 透明なトレイルとして表示する前のフレームの数。
  * `framerate::Integer=30`: アニメーションのフレームレート。
  * `color=:purple`: 原子の色。単一の色または原子の数と同じ長さの色のリストにすることができます。
  * `connection_color=:orange`: 結合の色。単一の色または`connections`と同じ長さの色のリストにすることができます。
  * `markersize=0.05`: データの単位での原子マーカーのサイズ。
  * `linewidth=2.0`: 結合線の幅。
  * `transparency=true`: プロットで透明度が有効かどうか。
  * `show_boundary::Bool=true`: 境界ボックスを線として表示するかどうか。
  * `boundary_linewidth=2.0`: 境界線の幅。
  * `boundary_color=:black`: 境界線の色。
  * `kwargs...`: その他のキーワード引数はポイントプロット関数に渡されます。
