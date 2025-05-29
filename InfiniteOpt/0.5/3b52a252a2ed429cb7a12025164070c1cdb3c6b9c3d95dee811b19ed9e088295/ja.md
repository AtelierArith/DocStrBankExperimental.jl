```
@infinite_parameter(model::InfiniteModel, kwargs...)
```

モデル `model` にキーワード引数 `kw_args` で説明される *匿名* 無限パラメータを追加し、パラメータ参照を返します。

```julia
@infinite_parameter(model::InfiniteModel, expr, kwargs...)
```

式 `expr` とキーワード引数 `kw_args` で説明されるモデル `model` に無限パラメータを追加します。（以下では、記号 `in` を `∈` の代わりに使用できます）式 `expr` は次の形式を取ることができます：

  * `paramexpr` は `paramexpr` で説明されるパラメータを作成します。
  * `paramexpr ∈ [lb, ub]` は `paramexpr` で説明されるパラメータを作成し、下限 `lb` と上限 `ub` を持つ連続区間ドメインによって特徴付けられます。
  * `paramexpr ~ dist` は `paramexpr` で説明されるパラメータを作成し、`Distributions.jl` の分布オブジェクト `dist` によって特徴付けられます。
  * `paramexpr ∈ domain` は `paramexpr` で説明されるパラメータを作成し、`AbstractInfiniteDomain` オブジェクト `domain` によって特徴付けられます。

式 `paramexpr` は次の形式を取ることができます：

  * `paramname` は名前 `paramname` のスカラー パラメータを作成します。
  * `paramname[...]` または `[...]` はパラメータのコンテナを作成します。

`kwargs` で認識されるキーワード引数は次のとおりです：

  * `base_name`: パラメータ名を生成するために使用される名前プレフィックスを設定します。スカラー パラメータの場合はパラメータ名に対応し、そうでない場合は各軸 `axes` のインデックス `...` に対して `base_name[...]` に設定されます。
  * `domain`: パラメータを特徴付ける `InfiniteDomain`。[`AbstractInfiniteDomain`](@ref) のサブタイプを参照してください。
  * `distribution`: パラメータを特徴付ける `Distributions.jl` の分布オブジェクトを設定します（ドメインの代わりに指定）。
  * `supports`: パラメータのサポートポイントを設定します。
  * `num_supports`: 自動生成されるサポートの数を指定します。`supports` が優先されることに注意してください。デフォルトは 0 です。
  * `derivative_method`: パラメータに関して取られる導関数を評価するための数値的方法を指定します。
  * `sig_digits`: 自動サポート生成に使用されるべき有効桁数を指定します。デフォルトは `DefaultSigDigits` です。
  * `independent`: 各パラメータが互いに独立しているかどうかを指定します。デフォルトは false です。
  * `container`: コンテナタイプを指定します。デフォルトは `Auto` です。

**例**

```julia-repl
julia> @infinite_parameter(m, x in [0, 1])
x

julia> @infinite_parameter(m, y[i = 1:2] ~ MvNormal(ones(2)), num_supports = 10)
2-element Array{GeneralVariableRef,1}:
 y[1]
 y[2]

julia> z = @infinite_parameter(m, [["a", "b"]], distribution = Normal(),
                               independent = true)
1-dimensional DenseAxisArray{GeneralVariableRef,1,...} with index sets:
    Dimension 1, ["a", "b"]
And data, a 2-element Array{GeneralVariableRef,1}:
 noname[a]
 noname[b]
```
