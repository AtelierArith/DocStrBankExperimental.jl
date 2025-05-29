```
n_points(body)
```

ボディ内のポイントの総数を返します。

# 引数

  * `body::Body`: [`Body`](@ref)。

# 戻り値

  * `n_points::Int`: ボディ内のポイントの数。

# 例

```julia-repl
julia> body = Body(BBMaterial(), pos, vol)
1000ポイントのボディ{BBMaterial{NoCorrection}}:
  1ポイントセット:
    1000ポイントセット `all_points`

julia> n_points(body)
1000
```

---

```
n_points(multibody_setup)
```

マルチボディセットアップ内のポイントの総数を返します。

# 引数

  * `multibody_setup::MultibodySetup`: [`MultibodySetup`](@ref)。

# 戻り値

  * `n_points::Int`: マルチボディセットアップ内のすべてのボディからのポイントの合計。

# 例

```julia-repl
julia> ms = MultibodySetup(:a => body_a, :b => body_b)
2000ポイントのマルチボディセットアップ:
  1000ポイントのボディ{BBMaterial{NoCorrection}} 名前 `a`
  1000ポイントのボディ{BBMaterial{NoCorrection}} 名前 `b`

julia> n_points(ms)
2000
```
