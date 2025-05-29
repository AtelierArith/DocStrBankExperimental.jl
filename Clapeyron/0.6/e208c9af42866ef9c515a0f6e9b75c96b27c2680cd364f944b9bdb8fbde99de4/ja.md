```
reference_state(model)::Union{ReferenceState,Nothing}
```

入力モデルの参照状態を返します。利用可能でない場合は `nothing` を返します。

## 例

```julia-repl
julia> reference_state(PCSAFT("water"))
false

julia> has_reference_state(PCSAFT("water",idealmodel = ReidIdeal))
true

julia> reference_state(PCSAFT("water",idealmodel = MonomerIdeal)) #参照状態があり、初期化されていません。
ReferenceState(String[], Float64[], Float64[], NaN, NaN, Float64[], Float64[], Float64[], :unknown, :no_set)

julia> reference_state(PCSAFT("water",idealmodel = MonomerIdeal, reference_state = ReferenceState(:nbp))) #初期化された参照状態があります
ReferenceState(["water"], [33107.133379491206], [17.225988924236503], NaN, NaN, [0.0], [0.0], [0.0], :unknown, :nbp)
```
