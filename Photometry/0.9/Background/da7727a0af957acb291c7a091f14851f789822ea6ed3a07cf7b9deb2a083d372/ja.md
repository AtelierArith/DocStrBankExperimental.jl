```
sigma_clip!(x, sigma; fill=:clamp, center=median(x), std=std(x))
sigma_clip!(x, sigma_low, sigma_high; fill=:clamp, center=median(x), std=std(x))
```

[`sigma_clip`](@ref) のインプレースバージョン

!!! warning
    `sigma_clip!` は要素をインプレースで変更し、変更は型の変更を引き起こすことはできません。入力の型に注意してください。もし `Int64` を使用していて、`0.5` にクリップしようとすると、`InexactError` が発生します。

    これを避けるために、クリッピングの前に浮動小数点数に変換するか、内部でこれを行う [`sigma_clip`](@ref) を使用することをお勧めします。

