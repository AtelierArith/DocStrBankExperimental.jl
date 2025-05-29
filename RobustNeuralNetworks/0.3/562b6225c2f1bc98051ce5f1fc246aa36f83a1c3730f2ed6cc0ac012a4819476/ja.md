```
REN(ps::AbstractRENParams{T}) where T
```

直接パラメータ化からRENを構築します。

このコンストラクタはRENの直接パラメータ化（例えば、[`GeneralRENParams`](@ref) インスタンス）を受け取り、RENの**呼び出し可能な**明示的パラメータ化に変換します。例は[`AbstractREN`](@ref)のドキュメントにあります。

他に[`AbstractREN`](@ref)、[`WrapREN`](@ref)、および[`DiffREN`](@ref)も参照してください。
