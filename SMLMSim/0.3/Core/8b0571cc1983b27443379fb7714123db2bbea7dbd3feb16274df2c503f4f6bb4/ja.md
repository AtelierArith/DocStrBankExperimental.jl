```
get_num_tracks(smld::BasicSMLD)
```

SMLD内のユニークなトラックの数（track_idに基づく）を返します。

# 引数

  * `smld::BasicSMLD`: 分析するSMLD

# 戻り値

  * `Int`: ユニークなトラックIDの数

# 例

```julia
# トラックの数を取得
n_tracks = get_num_tracks(smld)
```
