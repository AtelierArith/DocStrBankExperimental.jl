`Product`は、パッケージのビルドまたはインストール後に期待される結果です。

`Product`の例には、[`LibraryProduct`](@ref)、[`FrameworkProduct`](@ref)、[`ExecutableProduct`](@ref)、および[`FileProduct`](@ref)が含まれます。すべての`Product`タイプは、以下の最小限の機能セットを定義する必要があります。

  * [`locate(::Product)`](@ref): `Product`を与えられた場合、それをラップされた`Prefix`内で見つけ、その位置を文字列として返します
  * [`satisfied(::Product)`](@ref): `Product`を与えられた場合、それが正常に満たされているかどうかを判断します（例：見つけられ、すべてのコールバックを通過する）
  * [`variable_name(::Product)`](@ref): `Product`に割り当てられた変数名を返します
  * `repr(::Product)`: この`Product`の表現を返します。これは、`Products`を構築するソースコードを自動生成するのに役立ちます。あなたの好みであれば。
