```
generate(body, pre_substitution; eval_module, tl_opts)
```

パラメータ化された式の内包表現を展開して評価します。

!!! 注意: 式の中では、`$sym`の原子は`:(:sym)`としてエスケープする必要があります。

# 例

```
generate("{$a+$b, a=1:3, b=3:5, dlm=+, zip=true}")
generate(:({:($a)+:($b)+:($c), a=1:3, b=3:5, dlm=+, zip=true}), Dict(:c=>2))
```
