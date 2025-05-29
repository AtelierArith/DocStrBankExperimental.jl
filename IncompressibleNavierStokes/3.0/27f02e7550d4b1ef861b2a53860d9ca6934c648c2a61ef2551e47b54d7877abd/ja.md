```julia
velocityfield(setup, ufunc; ...) -> Any
velocityfield(setup, ufunc, t; psolver, doproject) -> Any

```

時間`t`における境界条件を持つ発散のない速度場`u`を作成します。`u[α]`の初期条件は関数`ufunc(α, x...)`によって指定されます。
