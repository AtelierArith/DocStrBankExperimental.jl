```julia
function fbands(sr :: Int,
                wl :: Int,
         bandwidth :: IntOrReal;
      DC :: Bool = false)
```

呼び出し時に作成されたビンに対応する周波数のベクトル（Hz単位）を返します。関数 [`bbands`](@ref) と同じ引数を使用します。

**参照**: [`bbands`](@ref).

**関連**: [`bands`](@ref).
