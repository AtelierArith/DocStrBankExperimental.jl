```
init(::Type{AHSG{N,HCP}}, pointSetProperties::SVector{N,Int})
```

スパースグリッドを初期化します。ルートポイントのみが作成された `N` 次元のスパースグリッドを返します。

# コンストラクタ

  * `::Type{AHSG{N,HCP}}`: [`DistributedSparseGrids.ASHG`](@ref) のタイプを定義します。
  * `pointSetProperties::SVector{N,Int}`: すべてのポイントセットプロパティを含むベクトル。

ポイントセットプロパティ = [psp*1,...,psp*N], psp_i は [1,2,3,4] のいずれか。 1=>`閉じたポイントセット`、 2=>`開いたポイントセット`、 3=>`左開きポイントセット`、 4=>`右開きポイントセット`。

# 例

N = 1; pointprobs = @SVector [1]; RT = Float64; CT = Float64; CPType = CollocationPoint{N,CT}; HCPType = HierarchicalCollocationPoint{N,CPType,RT}; asg = init(AHSG{N,HCPType},pointprobs) ```
