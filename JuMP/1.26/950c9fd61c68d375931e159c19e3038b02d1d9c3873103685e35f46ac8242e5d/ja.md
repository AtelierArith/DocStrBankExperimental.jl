```
object_dictionary(model::GenericModel)
```

変数、制約、または式のシンボル名を対応するオブジェクトにマッピングする辞書を返します。

オブジェクトはマクロ内の特定のシンボルに登録されます。例えば、`@variable(model, x[1:2, 1:2])`は変数の配列`x`をシンボル`:x`に登録します。

このメソッドは`AbstractModel`の任意のサブタイプに対して定義されるべきです。

参照: [`unregister`](@ref).

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> object_dictionary(model)
Dict{Symbol, Any} with 1 entry:
  :x => VariableRef[x[1], x[2]]
```
