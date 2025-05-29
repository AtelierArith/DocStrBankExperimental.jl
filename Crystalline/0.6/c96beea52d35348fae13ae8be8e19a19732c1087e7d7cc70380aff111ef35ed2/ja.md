```julia
littlegroup(
    sg::Crystalline.SpaceGroup,
    kv::Crystalline.KVec
) -> Crystalline.LittleGroup
littlegroup(
    sg::Crystalline.SpaceGroup,
    kv::Crystalline.KVec,
    klab::String
) -> Crystalline.LittleGroup

```

空間群 `sg` に関連するリトルグループを **k**-ベクトル `kv` で返します。

オプションとして、関連する **k**-ベクトルラベル `klab` を提供できます。提供されない場合は、空の文字列がラベルとして使用されます。
