欠損値のある観測データについて。

# コンストラクタ

```
SemObservedMissing(;
    data,
    observed_vars = nothing,
    specification = nothing,
    kwargs...)
```

# 引数

  * `data`: 観測データ
  * `observed_vars::Vector{Symbol}`: データの列名（データとして渡されたオブジェクトに列名がない場合、すなわちデータフレームでない場合）
  * `specification`: オプションのSEMモデル仕様（[`SemSpecification`](@ref)）

# 拡張ヘルプ

## インターフェース

  * `nsamples(::SemObservedMissing)` -> サンプル数（データポイント数）
  * `nobserved_vars(::SemObservedMissing)` -> 観測変数の数
  * `samples(::SemObservedMissing)` -> データ行列（測定値と欠損値の両方を含む）

## 期待値最大化

`em_mvn!(::SemObservedMissing)`は、マルチバリアント正規性の仮定の下で期待値最大化（EM）アルゴリズムを使用してデータに対して共分散行列と平均ベクトルをフィットさせるために呼び出すことができます。その後、以下のメソッドが利用可能です：

  * `em_model(::SemObservedMissing)` -> EMを通じて見つかった共分散行列と平均ベクトルを含む`EmMVNModel`
  * `obs_cov(::SemObservedData)` -> EM共分散行列
  * `obs_mean(::SemObservedData)` -> EM平均ベクトル
