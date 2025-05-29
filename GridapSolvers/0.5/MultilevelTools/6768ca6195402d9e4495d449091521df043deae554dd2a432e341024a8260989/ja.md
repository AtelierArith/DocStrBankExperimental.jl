```
CartesianModelHierarchy(
  ranks::AbstractVector{<:Integer},
  np_per_level::Vector{<:NTuple{D,<:Integer}},
  domain::Tuple,
  nc::NTuple{D,<:Integer};
  nrefs::Union{<:Integer,Vector{<:Integer},Vector{<:NTuple{D,<:Integer}},NTuple{D,<:Integer}},
  map::Function = identity,
  isperiodic::NTuple{D,Bool} = Tuple(fill(false,D)),
  add_labels!::Function = (labels -> nothing),
) where D
```

最も粗いレベルとして直交モデルを持つ `ModelHierarchy` を返します。i 番目のレベルは `np_per_level[i]` プロセッサに分配されます。2 つの連続するレベルは `nrefs[i]` の因子で細分化されます。

## パラメータ:

  * `ranks`: 初期コミュニケーター。サブコミュニケーターを生成するために使用されます。
  * `domain`: ドメインの制限を含むタプル。
  * `nc`: 最も粗いモデルの各方向のセル数を含むタプル。
  * `np_per_level`: 各レベルに分配したいプロセッサの数を含むベクター。各レベルに対してタプル `np = (np_1,...,np_d)` が必要であり、各レベルは `prod(np)` プロセッサに分配され、i 番目の方向には `np_i` プロセッサが配置されます。
  * `nrefs`: 各レベルの細分化因子を含むベクター。`nlevs-1` のエントリがあり、各エントリは整数（均一な細分化）または `D` 個の整数を持つタプル（非均一な細分化）であることができます。
