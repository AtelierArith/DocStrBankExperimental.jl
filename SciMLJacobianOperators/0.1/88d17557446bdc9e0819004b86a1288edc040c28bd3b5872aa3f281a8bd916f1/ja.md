```
JacobianOperator{iip, T} <: AbstractJacobianOperator{T} <: AbstractSciMLOperator{T}
```

ヤコビアンオペレーターは、可能であれば、いずれも具現化せずにJVPとVJPの両方を提供します。

### コンストラクタ

```julia
JacobianOperator(prob::AbstractNonlinearProblem, fu, u; jvp_autodiff = nothing,
    vjp_autodiff = nothing, skip_vjp::Val = Val(false), skip_jvp::Val = Val(false))
```

デフォルトでは、`JacobianOperator`は`JVP`を計算します。`Base.adjoint`または`Base.transpose`を使用して`VJP`に切り替えます。

### VJPの計算

VJPの計算は以下のルールに従って行われます：

  * `f`に`vjp`メソッドがある場合、それを使用します。
  * `f`に`jac`メソッドがあり、`vjp_autodiff`が提供されていない場合、`jac * v`を使用します。
  * `vjp_autodiff`が提供されている場合、DifferentiationInterface.jlを使用してVJPを計算します。

### JVPの計算

JVPの計算は以下のルールに従って行われます：

  * `f`に`jvp`メソッドがある場合、それを使用します。
  * `f`に`jac`メソッドがあり、`jvp_autodiff`が提供されていない場合、`v * jac`を使用します。
  * `jvp_autodiff`が提供されている場合、DifferentiationInterface.jlを使用してJVPを計算します。

### 特殊ケース（数値）

数値入力の場合、VJPとJVPは区別されません。したがって、`vjp`または`jvp`のいずれかが提供されている場合、それを使用します。どちらも提供されていない場合、`jac`が提供されている場合は`v * jac`を使用します。最後に、DifferentiationInterface.jlを使用して導関数を計算し、`v`で乗算するためにそれぞれの自動微分メソッドを使用します。

### 提供されるメソッド

!!! warning
    現在、問題構築中の`p`はオペレーター評価中の`p`と同じであることが期待されています。この制限は将来的に解除される予定です。


  * `(op::JacobianOperator)(v, u, p)`: `∂f(u, p)/∂u * v`または`∂f(u, p)/∂uᵀ * v`を計算します。
  * `(op::JacobianOperator)(res, v, u, p)`: `∂f(u, p)/∂u * v`または`∂f(u, p)/∂uᵀ * v`を計算し、結果を`res`に格納します。

[`VecJacOperator`](@ref)および[`JacVecOperator`](@ref)も参照してください。
