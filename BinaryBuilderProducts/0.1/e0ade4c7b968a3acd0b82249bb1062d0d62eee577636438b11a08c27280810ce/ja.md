`AbstractProduct`は、パッケージのビルド後に期待される結果です。

`Product`の例には、[`LibraryProduct`](@ref)、[`FrameworkProduct`](@ref)、[`ExecutableProduct`](@ref)、および[`FileProduct`](@ref)が含まれます。すべての`AbstractProduct`タイプは、以下の最小限の機能セットを定義する必要があります。

  * [`locate(product::AbstractProduct, prefix::String; env::Dict)`](@ref): 指定された`prefix`に対して製品の位置を特定し、その位置を文字列として返します。環境変数のテンプレート化は、指定された`env`辞書を使用して行われます。位置の特定に失敗した場合は`nothing`を返します。
  * [`variable_name(::AbstractProduct)`](@ref): 製品の指定された変数名を`Symbol`として返します。
