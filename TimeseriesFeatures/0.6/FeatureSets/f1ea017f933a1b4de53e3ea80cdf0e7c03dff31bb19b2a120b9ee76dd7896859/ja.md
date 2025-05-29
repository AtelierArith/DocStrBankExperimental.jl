```
FeatureSet(methods, [names, keywords, descriptions])
FeatureSet(features::Vector{T}) where {T <: AbstractFeature}
```

`methods`（関数のベクトル）から`FeatureSet`を構築し、オプションで`names`をシンボルのベクトル、`descriptions`を文字列のベクトル、`keywords`を文字列のベクトルのベクトルとして提供します。`FeatureSet`は、時間系列が列を占める時間系列ベクトルまたは行列`X`に対して呼び出すことができ、特徴値の`FeatureArray`を返します。`FeatureSet` `𝒇`の部分集合は、特徴名（シンボルとして）または通常の線形および論理インデックスでインデックス指定することによって取得できます。`FeatureSet`は、配列に対して定義された単純な集合演算（和集合や積集合など）をサポートし、連結（`+`）や集合の差（`\`）のための便利な構文も提供します。2つの特徴は、その名前が等しい場合に限り（`isequal`）、同じと見なされます。

# 例

```julia
𝒇 = FeatureSet([sum, length], [:sum, :length], ["∑x¹", "∑x⁰"], [["distribution"], ["sampling"]])
X = randn(100, 2) # 2つの時間系列、100サンプルの長さ
F = 𝒇(X)

# 特徴セットの結合
𝒇₁ = FeatureSet([x->min(x...), x->max(x...)], [:min, :max], ["minimum", "maximum"], [["distribution"], ["distribution"]])
𝒈₁ = 𝒇 + 𝒇₁
G = 𝒈₁(X)

# 特徴セットの交差、特徴はその名前によって排他的に識別される
𝒇₂ = FeatureSet(x->prod, :sum, "∏x", ["distributions"])
𝒈₂ = 𝒇 ∩ 𝒇₂ # それぞれ独自の:sumを持つ2つの特徴セットの交差
G = 𝒈₂(X) # 交差には、∩の最初の引数に対する:sumが含まれる; 𝒇
```
