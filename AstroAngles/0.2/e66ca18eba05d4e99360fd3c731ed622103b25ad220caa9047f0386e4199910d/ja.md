```
@hms_str
```

文字列を `"ha:min:sec"` 形式から角度に直接解析します。デフォルトではラジアンとして解析されますが、文字列の末尾にフラグを追加することで角度を選択できます。

  * `hms"..."rad` -> ラジアン (デフォルト)
  * `hms"..."deg` -> 度
  * `hms"..."ha` -> 時間角

# 例

```jldoctest
julia> hms"12:17:25.3"
3.2176090147193626

julia> hms"12:17:25.3"rad # デフォルト
3.2176090147193626

julia> hms"12:17:25.3"deg
184.35541666666666

julia> hms"12:17:25.3"ha
12.29036111111111
```

# 参照

[`parse_hms`](@ref)
