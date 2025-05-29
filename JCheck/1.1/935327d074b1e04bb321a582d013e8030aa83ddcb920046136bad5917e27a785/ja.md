```
Quickcheck(desc; rng=GLOBAL_RNG, n=100, serialize_fails=true)
```

型 [`Quickcheck`](@ref) のコンストラクタ。

# 引数

  * `desc::AbstractString`: インスタンスの説明
  * `rng::AbstractRNG`: 入力を生成するために使用される擬似乱数生成器
  * `n::Int`: 生成するランダム入力の数
  * `serialize_fails::Bool`: true の場合、失敗した入力を JLSO ファイルにシリアライズする

# 例

```jldoctest
julia> qc = Quickcheck("A Test")
A Test: 0 predicate and 0 free variable.
```
