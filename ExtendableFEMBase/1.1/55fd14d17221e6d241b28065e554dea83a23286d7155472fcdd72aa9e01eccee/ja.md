```julia
integrate(
    grid::ExtendableGrids.ExtendableGrid,
    AT::Type{<:ExtendableGrids.AssemblyType},
    integrand!,
    resultdim::Int64;
    T,
    kwargs...
) -> Union{Float64, Vector{Float64}}

```

統合は、次のシグネチャの積分関数の合計積分を返します

```
integrand!(result, qpinfo)
```

グリッドのエンティティATに対して。ここで、qpinfoは現在の数値点での情報にアクセスすることを可能にします。結果の長さはresultdimを介して指定する必要があります。

キーワード引数:

  * quadorder = 数値積分の次数を指定します（デフォルト = 0）
  * regions = これらの領域に積分を制限します（デフォルト = [] はすべての領域を意味します）
  * items = これらのアイテム番号に積分を制限します（デフォルト = [] はすべてのアイテムを意味します）
  * time = qpinfoに渡される時間を設定します（デフォルト = 0）
  * params = qpinfoに渡されるparams配列を設定します（デフォルト = []）
