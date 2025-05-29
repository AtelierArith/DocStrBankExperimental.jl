```julia
mutable struct Accumulator
```

不変の構造体に格納および更新できる可変イテレータ構造体。入力の累積値と現在の値を含みます。

# フィールド

  * `cumulative::Float64`: すべての入力の累積値。
  * `current::Float64`: 現在の入力値。
