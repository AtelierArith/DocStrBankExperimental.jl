```
basis([IntType], nbits::Int) -> UnitRange{IntType}
basis([IntType], state::AbstractArray) -> UnitRange{IntType}
```

nbits量子ビットのヒルベルト空間における基底のUnitRangeを返します。配列が供給されると、配列の最初の次元と同じサイズの基底が返されます。
