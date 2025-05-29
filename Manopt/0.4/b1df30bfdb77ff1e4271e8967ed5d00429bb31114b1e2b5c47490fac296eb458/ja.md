```
get_record(r::RecordGroup)
```

各タプルがイテレーションまたはレコード呼び出しごとの記録されたセットであるタプルの配列を返します。

```
get_record(r::RecordGruop, i::Int)
```

このレコードグループの `i` 番目のエントリに対応する値の配列を返します。

```
get_record(r::RecordGruop, s::Symbol)
```

`s` に関して記録された値の配列を返します。詳細は [`RecordGroup`](@ref) を参照してください。

```
get_record(r::RecordGroup, s1::Symbol, s2::Symbol,...)
```

各タプルがシンボル `s1, s2,...` に対応する記録されたセットであるタプルの配列を返します。
