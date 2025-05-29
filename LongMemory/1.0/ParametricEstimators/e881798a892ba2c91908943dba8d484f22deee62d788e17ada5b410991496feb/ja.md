```
my_toeplitz(coefs::Array)
```

与えられた係数からトペリッツ行列を構築します。

# 引数

  * `coefs::Array`: 係数の配列。

# 出力

  * `Toep::Array`: 与えられた係数から構築されたトペリッツ行列。

# 例

```julia
julia> my_toeplitz([1, 2, 3])
```
