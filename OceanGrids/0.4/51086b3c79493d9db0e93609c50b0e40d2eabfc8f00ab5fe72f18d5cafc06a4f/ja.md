```
interpolationmatrix(g, lats, lons, depths)
interpolationmatrix(g, obs)
```

スパース行列 `M` を返します。ここで `M*x` は、obs テーブルに提供された位置に補間されたモデルベクトル `x` です。

技術的には、これは線形補間を必要とし、`interpolation(x) = M * x` という形で表され、これは最近傍補間を必要とするようです。AIBECS がこの最近傍補間のみに依存するのであれば、Interpolations.jl を NearestNeighbors.jl に置き換えるのが良いかもしれません。また、モデルの土地（水ではなく）にある少数の観測値は破棄されます。

将来的には、より一般的なアプローチが、任意のタイプの補間のためにスパース対応の AD を使用し、海洋グリッドセル内にない位置で行われた観測を破棄しない補間を使用する予定です。
