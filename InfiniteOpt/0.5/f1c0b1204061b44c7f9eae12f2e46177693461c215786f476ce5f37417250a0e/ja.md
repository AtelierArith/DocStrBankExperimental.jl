```
@parameter_function(model::InfiniteModel, func_expr, kwargs...)
```

モデル `model` にキーワード引数 `kw_args` で説明される *匿名* パラメータ関数を追加し、オブジェクト参照を返します。

```julia
@parameter_function(model::InfiniteModel, var_expr == func_expr, kwargs...)
```

式 `var_expr`、関数式 `func_expr`、およびキーワード引数 `kwargs` で説明されるパラメータ関数を `model` に追加します。式 `var_expr` は、インデックスが他のマクロのコンテナ構文と一致する形のパラメータ関数参照 `varname[...]` を定義するために使用されます。

式 `func_expr` は、パラメータ関数の動作を定義する具体的な Julia 関数を決定し、またそれが依存する無限のパラメータを指定します。受け入れられる形式は次のとおりです：

  * `func(params...)`: ここで `func` は無限のパラメータ `params` のサポートを入力として受け取り、スカラー値を出力する関数です。
  * `(params...) -> my_func_expr`: ここで `params` は無限のパラメータで、`my_func_expr` は匿名関数のソースコードです。

`kwargs` で認識されるキーワード引数は次のとおりです：

  * `base_name`: オブジェクト名を生成するために使用される名前プレフィックスを設定します。スカラー パラメータ関数のオブジェクト名に対応し、そうでない場合は、オブジェクト名は各インデックス `...` の軸 `axes` に対して `base_name[...]` に設定されます。
  * `container`: コンテナタイプを指定します。デフォルトは `:Auto` です。

**例**

```julia-repl
julia> @parameter_function(model, sin(t))
sin(t)

julia> func_vect = [sin, cos];

julia> @parameter_function(model, [i = 1:2] == func_vect[i](t))
2-element Array{GeneralVariableRef,1}:
 sin(t)
 cos(t)

julia> f(t_val, x_vals) = t_val + sum(x_vals)
f (generic function with 1 method)

julia> @parameter_function(model, pf == f(t, x))
pf(t, x)

julia> g(t_val, a; b = 0) = t_val + a + b
g (generic function with 1 method)

julia> @parameter_function(model, pf2[i = 1:2] == t -> g(t, i, b = 2 * i ))
2-element Array{GeneralVariableRef,1}:
 pf2[1](t)
 pf2[2](t)
```
