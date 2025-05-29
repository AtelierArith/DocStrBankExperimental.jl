```
mutable struct ProjMPS2 <: AbstractProjMPO
    lpos::Int
    rpos::Int
    nsite::Int
    M::MPS
    LR::Vector{ITensor}
end
```

次のデータを保持します。ここで `psi` は最適化されている MPS であり、`M` は ProjMPS によって定数として保持される MPS です。

`ITensors.jl` の `AbstractProjMPO` から継承されています。

```
     o--o--o--o--o--o--o--o--o--o--o <M|
     |  |  |  |  |  |  |  |  |  |  |
     *--*--*-      -*--*--*--*--*--* |psi>
```

MPS のための射影演算子を計算するために必要です。
