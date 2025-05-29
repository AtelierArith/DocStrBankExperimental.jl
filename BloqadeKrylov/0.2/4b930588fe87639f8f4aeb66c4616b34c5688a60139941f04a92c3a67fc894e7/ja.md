```
CFETEvolution(reg, start_clock, durations, hamiltonian, options)
```

`CFETEvolution`オブジェクトを作成します。

# 引数

  * `reg`: レジスタオブジェクト。
  * `start_clock`: 進化の開始クロック。
  * `durations`: 各時間ステップでの持続時間のリスト。
  * `hamiltonian`: [`Hamiltonian`](@ref)型の低レベルハミルトニアンオブジェクト。
  * `options`: [`KrylovOptions`](@ref)型の進化のオプション。
