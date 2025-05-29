```
decompose(Ws::Vector{WitnessPoints}; options...)
```

この関数は、[`WitnessSet`](@ref) または [`WitnessSet`](@ref) のベクターを不可約成分に分解します。

### オプション

  * `show_progress = true`: 計算の進行状況を表示するかどうかを示します。
  * `show_monodromy_progress = false`: モノドロミ計算の進行状況を表示するかどうかを示します。
  * `monodromy_options`: [`monodromy_solve`](@ref) のための [`MonodromyOptions`](@ref)。
  * `max_iters = 50`: 分解ステップの最大反復回数。
  * `warning = true`: `true` の場合、[`trace_test`](@ref) が失敗したときに警告を表示します。
  * `threading = true`: 複数のスレッドを有効にします。
  * `seed`: ランダムシードを選択します。

### 例

以下の例は、2つの円の和集合のためのウィットネスセットを分解します。

```julia-repl
julia> @var x y
julia> f = (x^2 + y^2 - 1) * ((x-1)^2 + (y-1)^2 - 1)
julia> W = regeneration([f])
julia> decompose(W)
Numerical irreducible decomposition with 2 components
• 2 component(s) of dimension 1.

 degree table of components:
╭───────────┬───────────────────────╮
│ dimension │ degrees of components │
├───────────┼───────────────────────┤
│     1     │        (2, 2)         │
╰───────────┴───────────────────────╯
```
