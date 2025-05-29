```
@event f(arg...) T t [n]
```

クロックにイベントとして関数 `f(arg...)` をスケジュールします。

# 引数

  * `f`: イベント時に実行される関数、
  * `arg...`: その引数、最初の引数はクロックでなければなりません、
  * `T`: [`Timing`](@ref) （at, after, every）、
  * `t`: `Number` または `Distribution`、
  * `n::Int`: 繰り返しイベントの繰り返し回数。
