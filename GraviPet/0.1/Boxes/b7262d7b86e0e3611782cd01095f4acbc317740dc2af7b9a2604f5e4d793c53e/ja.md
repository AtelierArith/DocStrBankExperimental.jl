```
struct Box{D,T} <: Domain{SVector{D,T}}
```

多次元の [`Domains.Domain`](@ref)、すなわちボックスまたはハイパーレクタングル。次元数 `D` は非負の整数でなければなりません。`T` は `Float64` のような実数スカラー型であるべきです。ドメインの要素型は `SVector{D,T}` です。

ゼロ次元および一次元のドメインがサポートされています。ゼロ次元のドメインは単一の点（原点）のみを含みます。一次元のドメインは区間に対応します（[`Interval`](#GraviPet.Intervals.Interval)を参照）。
