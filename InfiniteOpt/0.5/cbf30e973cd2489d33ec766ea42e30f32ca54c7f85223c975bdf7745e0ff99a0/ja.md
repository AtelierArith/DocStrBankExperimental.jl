```
FiniteDifference{T <: FDTechnique} <: NonGenerativeDerivativeMethod
```

微分評価に適用される有限差分法に関する情報のための `DataType` です。コンストラクタは次の形式です：

```julia
    FiniteDifference([technique::FDTechnique = Backward()],
                     [add_boundary_constr::Bool = true])
```

ここで `technique` は適用される有限差分法を示し、`add_boundary_constr` は境界サポートに対応する有限差分方程式を含めるかどうかを示します。したがって、後方差分は端点に対応し、前方差分は初期点に対応します。後方法で最終条件が与えられている場合や、前方法で初期条件が与えられている場合は、`add_boundary_constr = false` を使用することをお勧めします。この引数は、境界点を含むことができない中央有限差分には無視されます。

**フィールド**

  * `technique::T`: 有限差分の背後にある数学的手法
  * `add_boundary_constraint::Bool`: 境界制約を転写に含めるべきかどうかを示します（例：後方差分のための端境界後方方程式）
