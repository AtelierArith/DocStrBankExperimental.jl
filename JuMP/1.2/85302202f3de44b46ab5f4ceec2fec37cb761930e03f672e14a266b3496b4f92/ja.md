```
@NLparameter(model, param == value)
```

モデル `model` に初期値 `value` を設定した非線形パラメータ `param` を作成して返します。非線形パラメータは非線形式のみに使用できます。

# 例

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, x == 10)
value(x)

# 出力
10.0
```

```
@NLparameter(model, value = param_value)
```

モデル `model` に初期値 `param_value` を設定した匿名の非線形パラメータ `param` を作成して返します。非線形パラメータは非線形式のみに使用できます。

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
x = @NLparameter(model, value = 10)
value(x)

# 出力
10.0
```

```
@NLparameter(model, param_collection[...] == value_expr)
```

モデル `model` に初期値 `value_expr` を設定した非線形パラメータのコレクション `param_collection` を作成して返します（インデックスセットに依存する場合があります）。インデックスセットを指定するための構文は [`@variable`](@ref) と同じです。

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
@NLparameter(model, y[i = 1:10] == 2 * i)
value(y[9])

# 出力
18.0
```

```
@NLparameter(model, [...] == value_expr)
```

モデル `model` に初期値 `value_expr` を設定した匿名の非線形パラメータのコレクションを作成して返します（インデックスセットに依存する場合があります）。インデックスセットを指定するための構文は [`@variable`](@ref) と同じです。

## 例

```jldoctest; setup=:(using JuMP)
model = Model()
y = @NLparameter(model, [i = 1:10] == 2 * i)
value(y[9])

# 出力
18.0
```
