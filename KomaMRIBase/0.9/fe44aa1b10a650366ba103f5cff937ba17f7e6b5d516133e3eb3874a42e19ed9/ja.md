```
gr = Grad(A, T)
gr = Grad(A, T, rise)
gr = Grad(A, T, rise, delay)
gr = Grad(A, T, rise, fall, delay)
gr = Grad(A, T, rise, fall, delay, first, last)
```

Grad構造体は、シーケンスイベントの勾配を表します。

# 引数

  * `A`: (`::Real`または`::Vector`, `[T/m]`) 勾配の振幅
  * `T`: (`::Real`または`::Vector`, `[s]`) フラットトップの持続時間
  * `rise`: (`::Real`, `[s]`) 上昇の持続時間
  * `fall`: (`::Real`, `[s]`) 下降の持続時間
  * `delay`: (`::Real`, `[s]`) 遅延の持続時間

# 戻り値

  * `gr`: (`::Grad`) 勾配構造体

# 例

```julia-repl
julia> gr = Grad(1, 1, 0.1, 0.1, 0.2)

julia> seq = Sequence([gr]); plot_seq(seq)
```
