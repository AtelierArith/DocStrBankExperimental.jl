```
unset_flag!(vi::VarInfo, vn::VarName, flag::String, ignorable::Bool=false
```

`vn`の`flag`の値を`vi`で`false`に設定します。

一部の`VarInfo`タイプに対してフラグを設定することはできず、デフォルトではその試みはエラーになります。`ignorable`が`true`に設定されている場合は、これが静かに無視されます。
