```
@set(opt, kwargs...)
```

`EC::ECInfo`のオプションを設定します。

最初の引数`opt`はオプションの名前です（例：`scf`、`cc`、`cholesky`）。詳細は[`ECInfos.Options`](@ref)を参照してください。キーワード引数は設定するオプションです（例：`thr=1.e-14`、`maxit=10`）。オプションの現在の状態は変数に保存できます。例えば、`opt_cc = @set cc`のようにします。その後、`@set cc opt_cc`で状態を復元できます。`EC`がまだ初期化されていない場合は、初期化されます。

# 例

```julia
optscf = @set scf thr=1.e-14 maxit=10
@set cc maxit=100
...
@set scf optscf
```
