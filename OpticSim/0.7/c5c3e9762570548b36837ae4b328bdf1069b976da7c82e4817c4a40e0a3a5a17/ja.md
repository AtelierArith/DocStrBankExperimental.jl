```
Interval{T} <: AbstractRayInterval{T}
```

レイ上の2つの [`IntervalPoint`](@ref) の間の区間を表すデータ型です。

下限要素は [`RayOrigin`](@ref) または [`Intersection`](@ref) のいずれかであることができます。上限要素は [`Intersection`](@ref) または [`Infinity`](@ref) のいずれかであることができます。

```julia
positivehalfspace(int::Intersection) -> Interval with lower = int, upper = Infinity
rayorigininterval(int::Intersection) -> Interval with lower = RayOrigin, upper = int
Interval(low, high)
```

次のアクセサメソッドがあります：

```julia
lower(a::Interval{T}) -> Union{RayOrigin{T},Intersection{T,3}}
upper(a::Interval{T}) -> Union{Intersection{T,3},Infinity{T}}
```
