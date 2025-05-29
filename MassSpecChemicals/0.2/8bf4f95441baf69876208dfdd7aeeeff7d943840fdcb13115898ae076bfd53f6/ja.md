```
getchemicalattr(chemical::AbstractChemical, attr::Symbol; kwargs...)
getchemicalattr(chemical::AbstractChemical, ::Val{T}; kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:formula}; shallow = false, kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:elements}; shallow = false, kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:charge}; kwargs...)
getchemicalattr(cc::AbstractChemical, ::Val{:abundant_chemical}; kwargs...)
```

属性（`attr`）を`chemical`から取得します。この関数はデフォルトで`attr`をプロパティ名として取り、プロパティを返します。`attr`が利用できない場合は、`nothing`を返します。

具体的な型`C <: AbstractChemical`と属性（`attr`）のために特定のメソッドを定義するには、次の関数シグネチャを使用します：

`getchemicalattr(::C, ::Val{attr}; kwargs...)`
