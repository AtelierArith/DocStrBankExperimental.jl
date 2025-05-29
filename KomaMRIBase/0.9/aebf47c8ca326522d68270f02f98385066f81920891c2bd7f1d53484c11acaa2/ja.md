```
delay = Delay(T)
```

Delay構造体は、合計演算子を使用してシーケンスに遅延を追加することを目的としています。

# 引数

  * `T`: (`::Real`, `[s]`) 時間遅延値

# 戻り値

  * `delay`: (`::Delay`) 遅延構造体

# 例

```julia-repl
julia> delay = Delay(0.5)

julia> s = Sequence([Grad(1, 1, 0.1)])

julia> seq = delay + s; plot_seq(seq)
```
