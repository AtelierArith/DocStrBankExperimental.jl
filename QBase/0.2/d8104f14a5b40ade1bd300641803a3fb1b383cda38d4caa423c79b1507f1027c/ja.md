`State` `ρ` を [`KrausChannel`](@ref) `𝒩` によって進化させます。

```
evolve(𝒩 :: KrausChannel, ρ :: State) :: State
evolve(𝒩 :: KrausChannel, ρ :: AbstractMatrix) :: Matrix
```

詳細については [`kraus_evolve`](@ref) メソッドを参照してください。
