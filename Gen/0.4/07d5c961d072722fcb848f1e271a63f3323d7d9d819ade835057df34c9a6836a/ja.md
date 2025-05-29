```
get_choices(trace)
```

割り当てインターフェースを実装する値を返します

アドレス指定されていないランダム性の値は外部からアクセスできないことに注意してください。

例:

```julia
choices::ChoiceMap = get_choices(trace)
z_val = choices[:z]
```
