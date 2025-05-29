```
IndependentParameter{T <: InfiniteScalarDomain,
                     M <: AbstractDerivativeMethod,
                     I <: AbstractGenerativeInfo} <: ScalarParameter
```

独立スカラー無限パラメータを格納するための `DataType`。

**フィールド**

  * `domain::T`: パラメータを特徴づける無限ドメイン。
  * `supports::DataStructures.SortedDict{Float64, Set{DataType}}`: パラメータを離散化するために使用されるサポートポイントと、それに関連するタイプラベルが `DataTypes` として格納されており、[`AbstractSupportLabel`](@ref) のサブタイプである必要があります。
  * `sig_digits::Int`: サポート値を丸めるために使用される有効桁数。
  * `derivative_method::M`: このパラメータに関して行われる導関数のために使用される導関数評価方法。
  * `gnerative_supp_info::I`: 既存のサポートに基づいて測定および/または導関数のために生成する必要がある任意の生成サポートに関連する情報。
