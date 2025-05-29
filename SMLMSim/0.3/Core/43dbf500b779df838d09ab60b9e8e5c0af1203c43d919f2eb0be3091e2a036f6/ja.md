```
get_tracks(smld::BasicSMLD)
```

トラックIDに基づいて、ユニークなトラックごとに1つのSMLDオブジェクトのベクターを返します。

# 引数

  * `smld::BasicSMLD`: 元のSMLD

# 戻り値

  * `Vector{BasicSMLD}`: トラックごとのSMLDオブジェクトのベクター

# 例

```julia
# すべてのトラックを別々のSMLDオブジェクトとして取得
track_smlds = get_tracks(smld)

# 最初のトラックにアクセス
first_track = track_smlds[1]
```
