```
periodic_system(atoms::AbstractVector, box; fractional=false, kwargs...)
```

すべての境界が `box` の周期的な [`FlexibleSystem`](@ref) を構築します（固体状態システムのモデル化のための標準設定）。`fractional` が true の場合、原子の座標は分数座標（および直交座標ではなく）で与えられます。追加の `kwargs` はカスタムシステムプロパティとして保存されます。

# 例

周期的境界条件内に水素分子を設定します：

```julia-repl
julia> cell_vectors = ([10.0, 0.0, 0.0]u"Å", [0.0, 10.0, 0.0]u"Å", [0.0, 0.0, 10.0]u"Å")
julia> hydrogen = periodic_system([:H => [0, 0, 1.]u"bohr",
                                   :H => [0, 0, 3.]u"bohr"],
                                  cell_vectors)
```

分数位置を使用してシリコン単位セルを設定します

```julia-repl
julia> box = 10.26 / 2 * [[0, 0, 1], [1, 0, 1], [1, 1, 0]]u"bohr"
julia> silicon = periodic_system([:Si =>  ones(3)/8,
                                  :Si => -ones(3)/8],
                                 box, fractional=true)
```
