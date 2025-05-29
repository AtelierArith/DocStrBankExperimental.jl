```
@enum VariableFunction
```

`:vfunction` 変数 [`Attribute`](@ref) の許可された値で、ホスト ODE または DAE ソルバーに対する変数関数を定義します。

dS/dt = F(S) の明示的 ODE 問題は、S::VF*StateExplicit と F::VF*Deriv 変数のペアで構成されます。

dU/dt = F(U) の暗黙的 ODE 問題では、総変数 U は状態変数 S の関数 U(S) であり、U::VF*Total と F::VF*Deriv 変数のペアで構成され、同じ数の S::VF_StateTotal も含まれます（特に順序はありません）。

代数制約 C(S) = 0 には、変数 C::VF*Constraint と同じ数の S::VF*State が含まれ、対応する VF_Deriv はありません。

すべてのソルバーがすべての組み合わせをサポートしているわけではありません。
