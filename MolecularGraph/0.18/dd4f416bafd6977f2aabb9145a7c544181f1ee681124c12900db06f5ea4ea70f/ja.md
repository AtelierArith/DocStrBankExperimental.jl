```
coordgen(mol::MolGraph) -> Tuple{Array{Int,1},Array{Int,1}}
```

シュレディンガーのcoordgenlibsを使用して2D座標を生成します。

これは`coords`と`styles`配列のタプルを返します。`coords`はサイズ(n, 2)の行列で、nは原子の数であり、各原子の2D座標(x, y)を格納します。`styles`はサイズeのベクトルで、eは結合の数であり、立体結合のウェッジ表記を含みます。
