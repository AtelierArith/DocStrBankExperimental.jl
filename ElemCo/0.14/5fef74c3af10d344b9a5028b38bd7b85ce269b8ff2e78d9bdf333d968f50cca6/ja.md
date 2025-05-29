```
@bohf()
```

FCIDUMP積分を使用して双直交HF計算を実行します。

軌道は[`WfOptions.orb`](@ref ECInfos.WfOptions)に保存されます。オープンシェル系（またはUHF FCIDUMP）の場合、BO-UHFエネルギーが計算されます。

# 例

```julia
fcidump = "FCIDUMP"
@bohf
```
