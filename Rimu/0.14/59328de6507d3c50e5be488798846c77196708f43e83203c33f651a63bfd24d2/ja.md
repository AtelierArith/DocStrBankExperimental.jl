```
ProjectedEnergy(hamiltonian, projector; hproj=:hproj, vproj=:vproj) <: PostStepStrategy
```

各ステップの後に、`hproj = dot(projector, hamiltonian, dv)` および `vproj = dot(projector, dv)` を計算します。ここで、`dv` は瞬時の係数ベクトルです。`projector` は [`AbstractDVec`](@ref) または [`AbstractProjector`](@ref) であることができます。

`hproj` および `vproj` の列に報告され、これはプロジェクティブエネルギーを計算するために使用できます。例えば、[`projected_energy`](@ref) を使用して計算できます。キーワード引数 `hproj` と `vproj` は、これらの列の名前を変更するために使用できます。これは、同じ実行で異なるプロジェクターを使用してプロジェクティブエネルギーを計算する際に、名前を一意にするために使用できます。

他にも [`projected_energy`](@ref)、[`ratio_of_means`](@ref)、[`mixed_estimator`](@ref)、および [`PostStepStrategy`](@ref) を参照してください。
