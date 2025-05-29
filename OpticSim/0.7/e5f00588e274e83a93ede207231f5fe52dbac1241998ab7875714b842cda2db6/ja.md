```
trace(assembly::LensAssembly{T}, r::OpticalRay{T}, temperature::T = 20.0, pressure::T = 1.0; trackrays = nothing, test = false)
```

アセンブリ内の任意の要素に当たった場合、[`LensTrace`](@ref) オブジェクトの形でアセンブリを出るときの光線を返します。そうでない場合は `nothing` を返します。再帰的な光線は、同じレンズ要素に即座に再交差するのを防ぐために、小さな量（`RAY_OFFSET`）だけオフセットされます。

`trackrays` には、アセンブリ内の表面との各交差点で `LensTrace` オブジェクトを蓄積するために空のベクターを渡すことができます。
