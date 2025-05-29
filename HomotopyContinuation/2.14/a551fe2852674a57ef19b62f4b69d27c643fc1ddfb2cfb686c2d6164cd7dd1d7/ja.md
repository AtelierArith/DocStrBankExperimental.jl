```
regeneration(F::System; options...)
```

これは、$F=0$ 方程式を方程式ごとに解決し、不可約成分に分解することなく、すべての次元に対して [`WitnessSet`](@ref) を返します（分解されていないウィットネスセットはウィットネススーパーセットとも呼ばれます）。

実装は、Duff、Leykin、Rodriguezによるアルゴリズム [u-regeneration](https://arxiv.org/abs/2206.02869) に基づいています。

### オプション

  * `sorted = true`: F の多項式は、次数の降順にソートされます。
  * `max_codim`: ウィットネススーパーセットを計算する最大コディメンション。
  * `show_progress = true`: 計算の進行状況を表示するかどうかを示します。
  * `endgame_options`: [`EndgameOptions`](@ref) for the [`EndgameTracker`](@ref).
  * `tracker_options`: [`TrackerOptions`](@ref) for the [`Tracker`](@ref).
  * `seed`: ランダムシードを選択します。

### 例

次の例は、2つの円の和集合に対するウィットネスセットを計算します。

```julia-repl
julia> @var x y
julia> f = (x^2 + y^2 - 1) * ((x-1)^2 + (y-1)^2 - 1)
julia> W = regeneration([f])
1-element Vector{WitnessSet}:
    Witness set for dimension 1 of degree 4  
```
