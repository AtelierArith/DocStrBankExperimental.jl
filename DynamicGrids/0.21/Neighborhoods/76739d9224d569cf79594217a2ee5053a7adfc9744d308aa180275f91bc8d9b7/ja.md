```
Positional <: AbstractPositionalNeighborhood

Positional(coord::Tuple{Vararg{Int}}...)
Positional(offsets::Tuple{Tuple{Vararg{Int}}})
Positional{O}()
```

任意の形状を取ることができる近傍で、中央点からの行/列の距離（正および負）を `Tuple{Int,Int}` で指定します。

近傍の半径は、最も遠い座標から計算されます。簡単のため、メイングリッドから読み取るウィンドウは、中央点の周りにある辺の長さが `2r + 1` の正方形です。

近傍の次元数 `N` は、最初の座標の長さから取られます。例えば、`1`、`2`、または `3` です。

例 半径 `R = 1`:

```
N = 1   N = 2

 ▄▄      ▀▄
          ▀
```

例 半径 `R = 2`:

```
N = 1   N = 2

         ▄▄
 ▀ ▀▀   ▀███
           ▀
```

`O` パラメータを使用することで、例えば `Positional{((1, 2), (1, 1))}()` は近傍を生成する際のランタイムコストを取り除きます。
