```
generate_supports(domain::AbstractInfiniteDomain
                  [method::Type{<:AbstractSupportLabel}];
                  [num_supports::Int = DefaultNumSupports,
                  sig_digits::Int = DefaultSigDigits]
                  )::Tuple{Array{<:Real}, DataType}
```

`domain`に従って`num_supports`のサポート値を`sig_digits`の有効桁数で生成し、それらを正しい生成ラベルと共に返します。`IntervalDomain`は`UniformGrid`ラベルで均等にサポートを生成し、分布ドメインは基礎となる分布に応じてランダムに生成します。さらに、`method`は使用すべき生成方法を示します。これらの`methods`はパラメータサポートラベルに対応しています。現在、生成方法として使用できるラベルには（特定のドメインタイプに対して定義されていない場合もありますが）以下が含まれます：

  * [`MCSample`](@ref): 均等に分布したモンテカルロサンプル。
  * [`WeightedSample`](@ref): 基礎となるPDFによって重み付けされたモンテカルロサンプル。
  * [`UniformGrid`](@ref): ドメイン全体で均等に生成されたサンプル。

ユーザー定義の無限ドメインタイプおよび/またはメソッドを使用する拡張は、これを可能にするために[`generate_support_values`](@ref)を拡張する必要があります。`domain`タイプおよび/またはメソッドが認識されない場合はエラーが発生します。これは、[`generate_and_add_supports!`](@ref)などのメソッドによって使用される内部メソッドとして意図されています。
