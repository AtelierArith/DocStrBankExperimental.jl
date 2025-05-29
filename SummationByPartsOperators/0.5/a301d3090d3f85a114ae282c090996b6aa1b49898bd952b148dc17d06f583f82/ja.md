```
PeriodicUpwindOperators
PeriodicUpwindOperators(D_minus, D_central, D_plus)
```

周期的アップウィンドSBPオペレーター用の個々のオペレーターを束ねた構造体です。個々のオペレーターは `D.minus`, `D.plus`（および提供されている場合はオプションで `D.central`）として利用可能で、ここで `D::PeriodicUpwindOperators` です。

結合された構造体は、曖昧さが生じない限り、オペレーター自体としてできるだけ多くの機能を持ちます。たとえば、アップウィンドオペレーターは同じグリッドと質量行列を使用する必要があるため、[`mass_matrix`](@ref), [`grid`](@ref), [`xmin`](@ref), [`xmax`](@ref) などが利用可能ですが、`mul!` は利用できません。

`PeriodicUpwindOperators` のインスタンスを [`upwind_operators`](@ref) を使用して構築することをお勧めします。インスタンスは、オペレーターを `D_minus, D_central, D_plus` の順に渡すことで手動で構築することもできます。

さらに [`upwind_operators`](@ref), [`UpwindOperators`](@ref) を参照してください。
