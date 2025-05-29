`State` `ρ` をチャネルの [`ChoiOp`](@ref) 表現 `Λ` によって進化させます。

```
evolve(Λ ::  ChoiOp, ρ :: State) :: State
evolve(Λ :: ChoiOp, ρ :: AbstractMatrix) :: Matrix
```

詳細については [`choi_evolve`](@ref) メソッドを参照してください。
