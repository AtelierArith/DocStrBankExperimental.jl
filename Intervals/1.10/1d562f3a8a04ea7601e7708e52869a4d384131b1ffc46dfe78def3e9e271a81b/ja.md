```
Interval{T, L <: Bound, R <: Bound}
```

`Interval`は、値の非反復可能な範囲またはスパンを表します（`StepRange`とは異なり、ステップが定義されていないため非反復可能です）。

`Interval`は、閉じた（`first`と`last`の両方が区間に含まれる）、開いた（`first`も`last`も含まれない）、または半開のいずれかです。この開放性は、型パラメータ`L`と`R`として保存される境界情報によって定義されます。

### 例

```julia
julia> interval = Interval{Closed,Open}(0, 100)
Interval{Int64,Closed,Open}}(0, 100)

julia> 0 in interval
true

julia> 50 in interval
true

julia> 100 in interval
false

julia> intersect(Interval{Open,Open}(0, 25), Interval{Closed,Closed}(20, 50)
Interval{Int64,Closed,Open}(20, 25)
```

### 中置コンストラクタ: `..`

閉じた`Interval`は、`..`中置コンストラクタを使用して構築できます：

```julia
julia> Dates.today() - Dates.Week(1) .. Dates.today()
Interval{Date,Closed,Closed}(2018-01-24, 2018-01-31)
```

関連情報: [`AnchoredInterval`](@ref)
