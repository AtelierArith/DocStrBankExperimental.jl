```
JuMPAlgorithm(optimizer)
```

JuMPインターフェースを使用して最近接相関行列問題を設定し解決するアルゴリズムです。オプティマイザは、半正定値プログラミングをサポートするものであれば何でも使用できます（[サポートされているソルバー](https://jump.dev/JuMP.jl/stable/installation/#Supported-solvers)を参照）。

## サポートされているオプティマイザ

このリストは網羅的ではなく、半正定値プログラミング（SDP）をサポートすることを明記したJuMPドキュメントに記載されている無料で利用可能なオプティマイザのみをテストしています。互換性のあるオプティマイザは、`PSD`制約もサポートする必要があります。

  * Clarabel.jl
  * COSMO.jl
  * ProxSDP.jl
  * SCS.jl
  * Hypatia.jl
  * Pajarito.jl

パフォーマンステストでは、COSMOが最も速いオプティマイザであり、次にSCSが速いです。また、COSMOオプティマイザに`"rho=>1.0"`を渡すことで収束を早めることをお勧めします。

## 例

```julia
using NearestCorrelationMatrix
using JuMP, Clarabel, COSMO, ProxSDP, SCS, Hypatia, Pajarito, HiGHS

# SCS.jl
alg = JuMPAlgorithm(SCS.Optimizer)

# COSMO.jl
alg = JuMPAlgorithm(COSMO.Optimizer)
opt = optimizer_with_attributes(COSMO.Optimizer, "rho" => 1.0)
alg = JuMPAlgorithm(opt)

# Pajarito.jl
opt = optimizer_with_attributes(
    Pajarito.Optimizer,
    "oa_solver" => optimizer_with_attributes(
        HiGHS.Optimizer,
        MOI.Silent() => true,
        "mip_feasibility_tolerance" => 1e-8,
        "mip_rel_gap" => 1e-6,
    ),
    "conic_solver" => optimizer_with_attributes(
        Hypatia.Optimizer,
        MOI.Silent() => true
    )
)
alg = JuMPAlgorithm(opt)
```
