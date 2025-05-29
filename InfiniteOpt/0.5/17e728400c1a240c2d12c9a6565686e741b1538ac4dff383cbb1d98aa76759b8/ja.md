```
@finite_parameter(model::InfiniteModel, value, kwargs...)
```

`model`に匿名の有限パラメータを定義して追加し、そのパラメータ参照を返します。値は`value`に等しいです。

```julia
@finite_parameter(model::InfiniteModel, param_expr == value_expr, kwargs...)
```

`model`に有限パラメータを定義して追加し、適切なパラメータ参照を返します。パラメータは`value_expr`で示された値を持ちます。`param_expr`の形式は次のようになります：

  * `paramname` はスカラーのパラメータ`paramname`を作成します。
  * `paramname[...]` または `[...]` はパラメータのコンテナを作成します。

`value_expr`は単にパラメータの値を表現します。通常は数値ですが、`param_expr`で定義されたインデックスを使用してインデックス付けされた配列である可能性もあります。

`kwargs`で認識されるキーワード引数は次のとおりです：

  * `base_name`: パラメータ名を生成するために使用される名前のプレフィックスを設定します。スカラーのパラメータ名に対応し、そうでない場合は、パラメータ名は各インデックス`...`の軸`axes`に対して`base_name[...]`に設定されます。
  * `container`: コンテナのタイプを指定します。デフォルトは`Auto`です。

**例**

```julia-repl
julia> par = @finite_parameter(model, 2)
noname

julia> vals = [3, 2];

julia> pars = @finite_parameter(model, [i = 1:2] == vals[i], base_name = "par")
2-element Array{ParameterRef,1}:
 par[1]
 par[2]

julia> @finite_parameter(model, par2 == 42)
par2
```
