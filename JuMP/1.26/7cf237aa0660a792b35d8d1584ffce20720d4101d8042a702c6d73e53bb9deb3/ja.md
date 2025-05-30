```
set_start_values(
    model::GenericModel;
    variable_primal_start::Union{Nothing,Function} = value,
    constraint_primal_start::Union{Nothing,Function} = value,
    constraint_dual_start::Union{Nothing,Function} = dual,
    nonlinear_dual_start::Union{Nothing,Function} = nonlinear_dual_start_value,
)
```

`model`内のプライマルおよびデュアルの開始値を提供された関数を使用して設定します。

任意のキーワード引数が`nothing`の場合、対応する開始値はスキップされます。

オプティマイザーが開始値の設定をサポートしていない場合、その値はスキップされます。

## `variable_primal_start`

この関数は、変数のプライマル開始解を制御します。これは、各変数に対して[`set_start_value`](@ref)を呼び出すことと同等であり、[`MOI.VariablePrimalStart`](@ref)属性を設定することと同等です。

関数である場合、`variable_primal_start(x::VariableRef)`の形式でなければならず、各変数`x`を開始プライマル値にマッピングします。

デフォルトは[`value`](@ref)です。

## `constraint_primal_start`

この関数は、制約のプライマル開始解を制御します。これは、各制約に対して[`set_start_value`](@ref)を呼び出すことと同等であり、[`MOI.ConstraintPrimalStart`](@ref)属性を設定することと同等です。

関数である場合、`constraint_primal_start(ci::ConstraintRef)`の形式でなければならず、各制約`ci`を開始プライマル値にマッピングします。

デフォルトは[`value`](@ref)です。

## `constraint_dual_start`

この関数は、制約のデュアル開始解を制御します。これは、各制約に対して[`set_dual_start_value`](@ref)を呼び出すことと同等であり、[`MOI.ConstraintDualStart`](@ref)属性を設定することと同等です。

関数である場合、`constraint_dual_start(ci::ConstraintRef)`の形式でなければならず、各制約`ci`を開始デュアル値にマッピングします。

デフォルトは[`dual`](@ref)です。

## `nonlinear_dual_start`

この関数は、非線形制約のデュアル開始解を制御します。これは、[`set_nonlinear_dual_start_value`](@ref)を呼び出すことと同等です。

関数である場合、`nonlinear_dual_start(model::GenericModel)`の形式でなければならず、制約のデュアル開始に対応するベクトルを返します。

デフォルトは[`nonlinear_dual_start_value`](@ref)です。
