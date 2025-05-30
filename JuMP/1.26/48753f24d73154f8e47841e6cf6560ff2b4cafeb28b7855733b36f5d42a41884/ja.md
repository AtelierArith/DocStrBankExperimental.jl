```
@NLparameter(model, param == value)
```

モデル `model` に初期値 `value` を設定した非線形パラメータ `param` を作成して返します。非線形パラメータは非線形式のみに使用できます。

## 例

```jldoctest
julia> model = Model();

julia> @NLparameter(model, x == 10)
x == 10.0

julia> value(x)
10.0
```

```
@NLparameter(model, value = param_value)
```

モデル `model` に初期値 `param_value` を設定した匿名の非線形パラメータ `param` を作成して返します。非線形パラメータは非線形式のみに使用できます。

## 例

```jldoctest
julia> model = Model();

julia> x = @NLparameter(model, value = 10)
parameter[1] == 10.0

julia> value(x)
10.0
```

```
@NLparameter(model, param_collection[...] == value_expr)
```

モデル `model` に初期値 `value_expr` を設定した非線形パラメータのコレクション `param_collection` を作成して返します（インデックスセットに依存する場合があります）。インデックスセットを指定するための構文は [`@variable`](@ref) と同じです。

## 例

```jldoctest
julia> model = Model();

julia> @NLparameter(model, y[i = 1:3] == 2 * i)
3-element Vector{NonlinearParameter}:
 parameter[1] == 2.0
 parameter[2] == 4.0
 parameter[3] == 6.0

julia> value(y[2])
4.0
```

```
@NLparameter(model, [...] == value_expr)
```

モデル `model` に初期値 `value_expr` を設定した匿名の非線形パラメータのコレクションを作成して返します（インデックスセットに依存する場合があります）。インデックスセットを指定するための構文は [`@variable`](@ref) と同じです。

!!! compat
    このマクロはレガシー非線形インターフェースの一部です。[非線形モデリング](@ref) に記載されている新しい非線形インターフェースの使用を検討してください。ほとんどの場合、`@NLparameter(model, p == value)` のような呼び出しを `@variable(model, p in Parameter(value))` に置き換えることができます。


## 例

```jldoctest
julia> model = Model();

julia> y = @NLparameter(model, [i = 1:3] == 2 * i)
3-element Vector{NonlinearParameter}:
 parameter[1] == 2.0
 parameter[2] == 4.0
 parameter[3] == 6.0

julia> value(y[2])
4.0
```
