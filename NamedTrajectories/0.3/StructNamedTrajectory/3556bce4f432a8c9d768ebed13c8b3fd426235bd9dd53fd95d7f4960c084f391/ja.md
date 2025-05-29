```
NamedTrajectory(data, components; kwargs...)

# 引数
- `data::AbstractMatrix{R}`: 軌道データ。
- `components::NamedTuple{names, <:Tuple{Vararg{AbstractVector{Int}}}} where names`: コンポーネントデータ。
- `kwargs...` : その他のキーワード引数。
```
