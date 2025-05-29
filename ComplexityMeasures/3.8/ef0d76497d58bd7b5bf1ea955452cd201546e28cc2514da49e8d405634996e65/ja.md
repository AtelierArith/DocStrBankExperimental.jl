```
OrdinalPatternEncoding <: Encoding
OrdinalPatternEncoding{m}(lt = ComplexityMeasures.isless_rand)
```

長さ`m`のベクトルをその順列/順序パターンにエンコードし、次にレーマーコードに基づいて整数にエンコードするスキームです。これは[`OrdinalPatterns`](@ref)や類似の推定器によって使用されており、結果空間の説明についてはそれを参照してください。

ベクトル`χ`の順序/順列パターンは単に`sortperm(χ)`であり、これは`χ`を昇順にソートするためのインデックスを返します。

## 説明

ここで実装されているレーマーコードは、長さ`m`のシーケンスに対する`factorial(m)`の可能な順列の集合と整数`1, 2, …, factorial(m)`との間の双射です。エンコードステップは、[Berger2019](@citet)のアルゴリズム1を使用しており、非常に最適化されています。デコードステップは最適化が不足しているため、はるかに遅くなります（プルリクエストは歓迎します！）。

## 例

```jldoctest
julia> using ComplexityMeasures

julia> χ = [4.0, 1.0, 9.0];

julia> c = OrdinalPatternEncoding(3);

julia> i = encode(c, χ)
3

julia> decode(c, i)
3-element SVector{3, Int64} with indices SOneTo(3):
 2
 1
 3
```

すでに順列パターンである何かをエンコードしたい場合は、非エクスポートの`permutation_to_integer`関数を使用できます。
