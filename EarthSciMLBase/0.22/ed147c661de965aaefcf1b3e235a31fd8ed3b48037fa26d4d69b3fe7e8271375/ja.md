オペレーターは、`Simulator` システムの現在の状態を変更するオブジェクトです。各オペレーターは、次のシグネチャを持つ関数を定義する必要があります。

```
`EarthSciMLBase.get_scimlop(::Operator, csys::CoupledSystem, mtk_sys, coord_args,
    domain::DomainInfo, u0, p, alg::MapAlgorithm)::AbstractSciMLOperator`
```

この関数は、[SciMLOperators.AbstractSciMLOperator](https://docs.sciml.ai/SciMLOperators/stable/interface/) を返す必要があります。オペレーターの定義方法についての詳細は、[SciMLOperators.jl](https://docs.sciml.ai/SciMLOperators/stable/) のドキュメントを参照してください。

オペレーターは、次のシグネチャを持つ関数も定義する必要があります。

```
`EarthSciMLBase.get_needed_vars(op::Operator, csys, mtk_sys, domain::DomainInfo)`
```

この関数は、オペレーターによって必要とされる変数のリストを返す必要があります。
