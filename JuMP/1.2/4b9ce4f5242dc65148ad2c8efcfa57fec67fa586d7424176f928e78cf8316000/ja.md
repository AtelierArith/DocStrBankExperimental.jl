```
unsafe_backend(model::Model)
```

JuMPモデル`model`に関連付けられた最も内側の最適化器を返します。

**この関数は、低レベルのソルバー固有の機能にアクセスしようとする上級ユーザーのみが使用すべきです。誤った使用のリスクが高いため、以下に示す代替手段を使用することを強くお勧めします。**

参照: [`backend`](@ref)。

## 安全でない動作

この関数は、主に2つの理由から安全ではありません。

まず、unsafe backendにおける変数や制約の定式化および順序は、`model`内の変数や制約とは異なる場合があります。これは、ブリッジが原因であったり、ソルバーが変数や制約を特定の順序で要求するために発生する可能性があります。さらに、JuMPレベルで[`index`](@ref)によって返される変数または制約のインデックスは、`unsafe_backend`内の対応する変数または制約のインデックスとは異なる場合があります。これに対する解決策はありません。代わりに、以下に示す代替手段を使用してください。

次に、`unsafe_backend`は空であるか、JuMPモデルに加えられた一部の変更が欠けている可能性があります。したがって、`unsafe_backend`を呼び出す前に、まず[`MOI.Utilities.attach_optimizer`](@ref)を呼び出して、バックエンドがJuMPモデルと同期していることを確認する必要があります。

```julia
MOI.Utilities.attach_optimizer(model)
inner = unsafe_backend(model)
```

さらに、JuMPモデルを変更した場合、バックエンドへの参照（上記の例では`inner`）が古くなっている可能性があり、再度[`MOI.Utilities.attach_optimizer`](@ref)を呼び出す必要があります。

この関数は逆方向でも安全ではありません。たとえば、`inner`に新しい制約を追加することによってunsafe backendを変更した場合、JuMPの`model`が変更または解決されると、変更が静かに破棄される可能性があります。

## 代替手段

`unsafe_backend`の代わりに、[`direct_model`](@ref)を使用してモデルを作成し、代わりに[`backend`](@ref)を呼び出してください。

たとえば、次のようにする代わりに:

```julia
model = Model(HiGHS.Optimizer)
@variable(model, x >= 0)
MOI.Utilities.attach_optimizer(model)
highs = unsafe_backend(model)
```

次のように使用します:

```julia
model = direct_model(HiGHS.Optimizer())
@variable(model, x >= 0)
highs = backend(model)  # `attach_optimizer`を呼び出す必要はありません。
```
