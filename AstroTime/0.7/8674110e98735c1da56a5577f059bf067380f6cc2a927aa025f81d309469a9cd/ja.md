```
@timescale scale [parent[, oneway]]
```

新しい時間スケールと対応する `Epoch` 型エイリアスを定義します。

### 引数

  * `scale`: 時間スケールの名前
  * `parent`: リンクする「親」時間スケール（オプション）
  * `oneway`: `true` の場合、`parent` から `scale` への変換のみが登録されます（オプション、デフォルト: `false`）

# 例

```jldoctest; setup = :(using AstroTime)
julia> @timescale GMT TAI

julia> GMT isa TimeScale
true

julia> GMTEpoch
Epoch{GMTScale}

julia> find_path(TT, GMT)
3-element Vector{TimeScale}:
 TT
 TAI
 GMT
```
