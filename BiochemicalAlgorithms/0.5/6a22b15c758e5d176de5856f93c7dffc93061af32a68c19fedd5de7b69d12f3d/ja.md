```
atom_by_name(
    ac::AbstractAtomContainer{T} = default_system(),
    name::AbstractString
) -> Union{Nothing, Atom{T}}
```

指定された `name` に関連付けられた最初の `Atom{T}` を `ac` から返します。該当する原子が存在しない場合は何も返しません。

# サポートされているキーワード引数

  * `frame_id::MaybeInt = 1`: `nothing` 以外の任意の値は、結果をこのフレーム ID に一致する原子に制限します。
