```
call_variant(
    pileup::VariationPileup,
    α::Float64;
    D::Union{Nothing,Int}=nothing,
    Q::Union{Nothing,Float64}=nothing,
    X::Union{Nothing,Float64}=nothing,
    F::Union{Nothing,Float64}=nothing,
    S::Union{Nothing,Float64}=nothing,
) -> VariationCall
```

`pileup` からバリアントを呼び出します。

# 引数

  * `pileup::VariationPileup`: バリアントを呼び出すためのパイルアップ
  * `α::Float64`: バリアントを呼び出すためのフィッシャーの正確な検定の有意水準 ($α$)

# キーワード

!!! note
    フィルタリングをスキップするために、未定義のキーワードはそのフィールドに基づいてスキップしてください


  * `D::Union{Nothing,Int}=nothing`: バリアントを呼び出すための最小総リード深度
  * `Q::Union{Nothing,Float64}=nothing`: バリアントを呼び出すための最小平均フレッド品質
  * `X::Union{Nothing,Float64}=nothing`: バリアントが呼び出されるためにリードの端から最大平均距離
  * `F::Union{Nothing,Float64}=nothing`: バリアントを呼び出すための最小代替頻度
  * `S::Union{Nothing,Float64}=nothing`: バリアントが一方のストランドに対して出現できる最大割合
