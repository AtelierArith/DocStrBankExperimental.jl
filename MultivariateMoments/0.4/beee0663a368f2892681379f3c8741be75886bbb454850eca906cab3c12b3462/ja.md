```
struct MomentVectorWeightSolver{T}
    rtol::T
    atol::T
end
```

与えられたモーメント行列 `ν` と原子中心に対して、まずモーメント行列をモーメントのベクトルに変換します。これは、[`measure(ν; rtol=rtol, atol=atol)`](@ref measure) を使用して行い、その後、得られた単項式に対して線形システムを解くことで重みを決定します。

同じ単項式に対応するモーメント値が小さな違いを持つ可能性がある場合、[`measure`](@ref) は `rtol` と `atol` が十分に小さくないとエラーを投げることがあります。これらの許容値を調整する代わりに、[`MomentVectorWeightSolver`](@ref) を使用することができます。
