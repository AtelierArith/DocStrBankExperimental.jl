```julia
ode_def_opts(name::Symbol, opts::Dict{Symbol, Bool}, curmod, ex::Expr, params...;
    depvar = :t)
```

コア内部。ユーザーは `@ode_def_*` マクロを通じてのみこれと対話するべきです。

オプションは `ODEFunction` への名前マッピングによって自己説明的です：

  * build_tgrad
  * build_jac
  * build_expjac
  * build_invjac
  * build_invW
  * build*invW*t
  * build_hes
  * build_invhes
  * build_dpfuncs

`depvar` は従属変数のシンボルを設定します。

例：

```julia
opts = Dict{Symbol, Bool}(:build_tgrad => true,
    :build_jac => true,
    :build_expjac => false,
    :build_invjac => true,
    :build_invW => true,
    :build_invW_t => true,
    :build_hes => false,
    :build_invhes => false,
    :build_dpfuncs => true)
```
