```
iso_id([db::SQLite.DB,] M::T, I::T) where T <: Union{Integer, AbstractVector{Integer}}
```

指定された分子IDと、単一の値または両方のパラメータに対して配列として提供されたローカルIDに対するグローバル同位体類似体IDを返します。

# 引数

  * `M`: 分子IDまたはIDの配列
  * `I`: ローカル同位体類似体IDまたはIDの配列
