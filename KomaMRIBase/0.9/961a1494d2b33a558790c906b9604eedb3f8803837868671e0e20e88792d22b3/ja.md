```
rf = RF(A, T)
rf = RF(A, T, Δf)
rf = RF(A, T, Δf, delay)
```

RF構造体は、シーケンスイベントのラジオ周波数励起を表します。

# 引数

  * `A`: (`::Complex`, `[T]`) RF複素振幅変調 (AM)、$B_1(t) = |B_1(t)|   e^{i\phi(t)} = B_{1}(t) + iB_{1,y}(t)$
  * `T`: (`::Real`, [`s`]) RFの持続時間
  * `Δf`: (`::Real`または`::Vector`, [`Hz`]) ラーマー周波数に対するRF周波数差。これは数値でも、周波数変調信号 (FM) を表すベクトルでもかまいません。
  * `delay`: (`::Real`, [`s`]) RF遅延時間

# 戻り値

  * `rf`: (`::RF`) RF構造体

# 例

```julia-repl
julia> rf = RF(1, 1, 0, 0.2)

julia> seq = Sequence(); seq += rf; plot_seq(seq)
```
