```
@variable(model, expr, args..., kw_args...)
```

モデル `model` に、式 `expr`、位置引数 `args`、およびキーワード引数 `kw_args` で説明される変数を追加します。

## 無名変数と名前付き変数

`expr` は次のいずれかの形式でなければなりません：

  * 省略された形、例えば `@variable(model)` は無名変数を作成します
  * 単一のシンボル、例えば `@variable(model, x)`
  * コンテナ式、例えば `@variable(model, x[i=1:3])`
  * 無名コンテナ式、例えば `@variable(model, [i=1:3])`

## 範囲

さらに、式には範囲を持たせることができます。例えば：

  * `@variable(model, x >= 0)`
  * `@variable(model, x <= 0)`
  * `@variable(model, x == 0)`
  * `@variable(model, 0 <= x <= 1)`

また、範囲はコンテナ式のインデックスに依存することができます：

  * `@variable(model, -i <= x[i=1:3] <= i)`

## 集合

変数が属する集合を明示的に指定することができます：

  * `@variable(model, x in MOI.Interval(0.0, 1.0))`

この構文に関する詳細は、[Variables constrained on creation](@ref)を参照してください。

## 位置引数

`args` で認識される位置引数は次のとおりです：

  * `Bin`: 変数を [`MOI.ZeroOne`](@ref) 集合、すなわち `{0, 1}` に制限します。例えば、`@variable(model, x, Bin)`。注意：`@variable(model, Bin)` は使用できません。代わりに `binary` キーワードを使用してください。
  * `Int`: 変数を整数の集合に制限します。すなわち、..., -2, -1,  0, 1, 2, ... 例えば、`@variable(model, x, Int)`。注意：`@variable(model, Int)` は使用できません。代わりに `integer` キーワードを使用してください。
  * `Symmetric`: 変数の正方行列を作成する際にのみ利用可能です。すなわち、`expr` が `varname[1:n,1:n]` または `varname[i=1:n,j=1:n]` の形式である場合、対称行列の変数を作成します。
  * `PSD`: `Symmetric` に制約を加えたもので、正方行列の変数を `Symmetric` に制約し、正定値半定義であることを制約します。

## キーワード引数

すべてのケースで便利な4つのキーワード引数があります：

  * `base_name`: 変数名を生成するために使用される名前のプレフィックスを設定します。スカラー変数の場合は変数名に対応し、そうでない場合は各インデックス `...` の軸 `axes` に対して `base_name[...]` に設定されます。
  * `start::Float64`: 各変数に対して `set_start_value` に渡される値を指定します。
  * `container`: コンテナの型を指定します。詳細は [Forcing the container type](@ref variable_forcing) を参照してください。
  * `set_string_name::Bool = true`: [`MOI.VariableName`](@ref) 属性を設定するかどうかを制御します。`set_string_name = false` を渡すことでパフォーマンスが向上する可能性があります。

無名変数との状況を明確にするために他のキーワード引数が必要です：

  * `lower_bound::Float64`: `x >= lb` の代替として、変数の下限値を設定します。
  * `upper_bound::Float64`: `x <= ub` の代替として、変数の上限値を設定します。
  * `binary::Bool`: `Bin` を渡す代替として、変数がバイナリであるかどうかを設定します。
  * `integer::Bool`: `Int` を渡す代替として、変数が整数であるかどうかを設定します。
  * `set::MOI.AbstractSet`: `x in set` を使用する代替として。
  * `variable_type`: JuMP 拡張によって使用されます。詳細は [Extend `@variable`](@ref extend_variable_macro) を参照してください。

## 例

次の方法は、下限が0の名前 `x` の変数 `x` を作成する同等の方法です：

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0)
x
```

```jldoctest
julia> model = Model();

julia> @variable(model, x, lower_bound = 0)
x
```

```jldoctest
julia> model = Model();

julia> x = @variable(model, base_name = "x", lower_bound = 0)
x
```

他の例：

```jldoctest
julia> model = Model();

julia> @variable(model, x[i=1:3] <= i, Int, start = sqrt(i), lower_bound = -i)
3-element Vector{VariableRef}:
 x[1]
 x[2]
 x[3]

julia> @variable(model, y[i=1:3], container = DenseAxisArray, set = MOI.ZeroOne())
1-dimensional DenseAxisArray{VariableRef,1,...} with index sets:
    Dimension 1, Base.OneTo(3)
And data, a 3-element Vector{VariableRef}:
 y[1]
 y[2]
 y[3]

julia> @variable(model, z[i=1:3], set_string_name = false)
3-element Vector{VariableRef}:
 _[7]
 _[8]
 _[9]
```
