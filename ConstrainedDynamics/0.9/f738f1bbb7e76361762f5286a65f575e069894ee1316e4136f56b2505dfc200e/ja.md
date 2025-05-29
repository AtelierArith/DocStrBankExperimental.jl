```julia
struct Storage{T, N}
```

`Storage`は、[`Mechanism`](@ref)のシミュレーション結果を保存するために使用できます。

インデックスの例:     storage.x[body*id][time*step_number][2] # 指定された時間ステップで指定されたボディのy位置を返します。

# 重要な属性

  * `x`: 各ボディと各時間ステップの位置を含みます。
  * `q`: 各ボディと各時間ステップの向きを含みます。
  * `v`: 各ボディと各時間ステップの速度を含みます。
  * `ω`: 各ボディと各時間ステップの角速度を含みます。

# コンストラクタ

```
Storage{T}(step_range, nbodies)
Storage(step_range, nbodies)
Storage{T}(nsteps, nbodies)
Storage(nsteps, nbodies)
```
