```
hashn!([T = UInt128], data::Vector{UInt8}; seed::UInt8 = 0)::T where T
```

データに対して（`n == sizeof(T)` の場合）`8*n` ビットのハッシュを計算します（オプションで `seed` を指定できます）。*注意:* `data` はインプレースで変更されます。変更なしのバージョンについては `hashn` を参照してください。
