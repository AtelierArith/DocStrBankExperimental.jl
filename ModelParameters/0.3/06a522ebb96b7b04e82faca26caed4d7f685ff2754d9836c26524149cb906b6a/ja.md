パラメータの抽象スーパークラス。これらは、[`params`](@ref) から返されるモデルパラメータ値とメタデータのラッパーであり、`getfield/setfield/getpropery/setproperty` メソッドで使用され、Tables.jl インターフェースを生成するために使用されます。これらは、[`stripparams`](@ref) を使用してモデルから削除されます。

`AbstractParam` は、`NamedTuple` を返す `Base.parent` メソッドと、`NamedTuple` を受け取るコンストラクタを定義する必要があります。また、`val` プロパティを持ち、コンストラクタ内で `checkhasval` を使用する必要があります。
