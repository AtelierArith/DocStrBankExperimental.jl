```
get_track(smld::BasicSMLD, id::Int)
```

指定された track_id のエミッターのみを含む新しい SMLD を返します。

# 引数

  * `smld::BasicSMLD`: 元の SMLD
  * `id::Int`: フィルタリングするトラック ID

# 戻り値

  * `BasicSMLD`: 指定されたトラックのエミッターのみを含む新しい SMLD

# 例

```julia
# トラック 5 に属するすべてのエミッターを取得
track_smld = get_track(smld, 5)
```
