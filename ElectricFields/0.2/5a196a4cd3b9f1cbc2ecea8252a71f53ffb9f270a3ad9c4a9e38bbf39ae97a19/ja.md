```
DispersedField(f, de, B, s)
```

フィールド `f` が [`DispersiveElement`](@ref) `de` を通じて分散されていることを表します。分散は周波数領域で最も効率的に計算されるため、これは [`rfft`](@ref)/[`irfft`](@ref) を介して行われ、分散されたフィールドは [`BSplineField`](@ref) `B` として補間されます。分散されたフィールドの時間的 [`span`](@ref) は `s` で与えられます。
