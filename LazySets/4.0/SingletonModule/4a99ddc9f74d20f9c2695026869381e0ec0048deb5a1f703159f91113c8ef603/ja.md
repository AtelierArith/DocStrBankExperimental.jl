```
Singleton{N, VN<:AbstractVector{N}} <: AbstractSingleton{N}
```

単一要素を持つ集合を表す型。

### フィールド

  * `element` – 集合の唯一の要素

### 例

```jldoctest
julia> Singleton([1.0, 2.0])
Singleton{Float64, Vector{Float64}}([1.0, 2.0])

julia> Singleton(1.0, 2.0)  # 数値からの便利なコンストラクタ
Singleton{Float64, Vector{Float64}}([1.0, 2.0])
```
