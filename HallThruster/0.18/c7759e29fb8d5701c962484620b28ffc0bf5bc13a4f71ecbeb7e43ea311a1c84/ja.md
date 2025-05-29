```julia
load_magnetic_field!(
    magnetic_field::HallThruster.MagneticField;
    include_dirs
)

```

空の `z` または `B` フィールドを持つ磁場 `field` が与えられた場合、`field.file` における磁場を探します。現在のディレクトリまたは提供された `include_dirs` のいずれかに見つかった場合、`z` と `B` をそれに応じて設定します。見つからない場合は ArgumentError をスローします。
