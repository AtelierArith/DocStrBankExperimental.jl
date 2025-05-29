```
numerical_irreducible_decomposition(F::System; options...)
```

$$
F=0
$$

で定義される多様体の数値的不可約分解を計算します。

### オプション

  * `show_progress = true`: 計算の進行状況を表示するかどうかを示します。
  * `show_monodromy_progress = false`: モノドロミ計算の進行状況を表示するかどうかを示します。
  * `sorted = true`: Fの多項式は次数の降順にソートされます。
  * `max_codim`: 証人スーパーセットが計算される最大コディメンション。
  * `endgame_options`: [`EndgameOptions`](@ref) for the [`EndgameTracker`](@ref).
  * `tracker_options`: [`TrackerOptions`](@ref) for the [`Tracker`](@ref).
  * `monodromy_options`: [`MonodromyOptions`](@ref) for [`monodromy_solve`](@ref).
  * `max_iters = 50`: 分解ステップの最大反復回数。
  * `warning = true`: `true`の場合、[`trace_test`](@ref)が失敗したときに警告を表示します。
  * `threading = true`: 複数のスレッドを有効にします。
  * `seed`: ランダムシードを選択します。

### 例

次の例は、次数2の1つの2次元成分、次数4の2つの1次元成分、および8つの点の和集合のための証人集合を計算します。

```julia-repl
julia> @var x, y, z
julia> p = (x * y - x^2) + 1 - z
julia> q = x^4 + x^2 - y - 1
julia> F = [p * q * (x - 3) * (x - 5);
            p * q * (y - 3) * (y - 5);
            p * (z - 3) * (z - 5)]

julia> N = numerical_irreducible_decomposition(F)
Numerical irreducible decomposition with 11 components
• 1 component(s) of dimension 2.
• 2 component(s) of dimension 1.
• 8 component(s) of dimension 0.

 degree table of components:
╭───────────┬──────────────────────────╮
│ dimension │  degrees of components   │
├───────────┼──────────────────────────┤
│     2     │            2             │
│     1     │          (4, 4)          │
│     0     │ (1, 1, 1, 1, 1, 1, 1, 1) │
╰───────────┴──────────────────────────╯
```
