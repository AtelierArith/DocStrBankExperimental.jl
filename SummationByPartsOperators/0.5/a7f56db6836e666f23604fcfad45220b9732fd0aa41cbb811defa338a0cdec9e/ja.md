```
UpwindOperators
UpwindOperators(D_minus, D_central, D_plus)
```

非周期的アップウィンドSBPオペレーターに利用可能な個々のオペレーターを束ねた構造体です。個々のオペレーターは `D.minus`, `D.plus`（および提供されている場合はオプションで `D.central`）として利用可能で、ここで `D::UpwindOperators` です。

結合された構造体は、曖昧さが生じない限り、できるだけオペレーター自体として振る舞います。たとえば、アップウィンドオペレーターは同じグリッドと質量行列を使用する必要があるため、[`mass_matrix`](@ref), [`grid`](@ref), [`xmin`](@ref), [`xmax`](@ref) などが利用可能ですが、`mul!` は利用できません。

`UpwindOperators` のインスタンスを構築するには、[`upwind_operators`](@ref) を使用することをお勧めします。インスタンスは、オペレーターを `D_minus, D_central, D_plus` の順に渡すことで手動で構築することもできます。

他にも [`upwind_operators`](@ref), [`PeriodicUpwindOperators`](@ref) を参照してください。
