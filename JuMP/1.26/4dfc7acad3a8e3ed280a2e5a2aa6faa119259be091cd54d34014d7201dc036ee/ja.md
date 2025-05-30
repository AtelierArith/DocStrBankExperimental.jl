```
unsafe_backend(model::GenericModel)
```

JuMPモデル`model`に関連付けられた最も内側のオプティマイザを返します。

**この関数は、低レベルのソルバー固有の機能にアクセスしようとする上級ユーザーのみが使用すべきです。誤った使用のリスクが高いため、以下に示す代替手段を使用することを強くお勧めします。**

参照: [`backend`](@ref)。

unsafe backend内の変数または制約のインデックスを取得するには、[`optimizer_index`](@ref)を使用します。

## 安全でない動作

この関数は、主に2つの理由で安全ではありません。

まず、unsafe backend内の変数と制約の定式化および順序は、`model`内の変数と制約とは異なる場合があります。これは、ブリッジのため、またはソルバーが変数または制約を特定の順序で要求するために発生する可能性があります。さらに、JuMPレベルで[`index`](@ref)によって返される変数または制約のインデックスは、`unsafe_backend`内の対応する変数または制約のインデックスとは異なる場合があります。これに対する解決策はありません。代わりに、以下に示す代替手段を使用してください。

第二に、`unsafe_backend`は空であるか、JuMPモデルに加えられた一部の変更が欠けている可能性があります。したがって、`unsafe_backend`を呼び出す前に、まず[`MOI.Utilities.attach_optimizer`](@ref)を呼び出して、バックエンドがJuMPモデルと同期していることを確認する必要があります。

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer)
A JuMP Model
├ solver: HiGHS
├ objective_sense: FEASIBILITY_SENSE
├ num_variables: 0
├ num_constraints: 0
└ Names registered in the model: none

julia> MOI.Utilities.attach_optimizer(model)

julia> inner = unsafe_backend(model)
A HiGHS model with 0 columns and 0 rows.
```

さらに、JuMPモデルを変更した場合、バックエンドへの参照（上記の例では`inner`）が古くなっている可能性があり、再度[`MOI.Utilities.attach_optimizer`](@ref)を呼び出す必要があります。

この関数は逆方向でも安全ではありません。たとえば、`inner`に新しい制約を追加することによってunsafe backendを変更した場合、JuMPの`model`が変更または解決されると、変更が静かに破棄される可能性があります。

## 代替手段

`unsafe_backend`の代わりに、[`direct_model`](@ref)を使用してモデルを作成し、代わりに[`backend`](@ref)を呼び出します。

たとえば、次のようにする代わりに:

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> MOI.Utilities.attach_optimizer(model)

julia> highs = unsafe_backend(model)
A HiGHS model with 1 columns and 0 rows.

julia> optimizer_index(x)
MOI.VariableIndex(1)
```

次のように使用します:

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> highs = backend(model)  # `attach_optimizer`を呼び出す必要はありません。
A HiGHS model with 1 columns and 0 rows.

julia> index(x)
MOI.VariableIndex(1)
```
