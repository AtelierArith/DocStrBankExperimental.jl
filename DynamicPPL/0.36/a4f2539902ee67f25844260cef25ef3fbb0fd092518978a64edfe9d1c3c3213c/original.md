```
unset_flag!(vi::VarInfo, vn::VarName, flag::String, ignorable::Bool=false
```

Set `vn`'s value for `flag` to `false` in `vi`.

Setting some flags for some `VarInfo` types is not possible, and by default attempting to do so will error. If `ignorable` is set to `true` then this will silently be ignored instead.
