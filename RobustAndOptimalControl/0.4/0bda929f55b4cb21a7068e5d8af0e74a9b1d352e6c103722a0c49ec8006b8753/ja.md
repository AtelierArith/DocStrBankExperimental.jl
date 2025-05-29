```
n, hsv = hankelnorm(sys::LTISystem; kwargs...)
```

ハンケルノルムとハンケル特異値を計算します

キーワード引数については、以下に再現された `DescriptorSystems.ghanorm` のドキュメントを参照してください。Base.Docs.DocStr(svec("    ghanorm(sys, fast = true, atol = 0, atol1 = atol, atol2 = atol, rtol = n*ϵ) -> (hanorm, hs)\n\n適切で安定した記述子システム `sys = (A-λE,B,C,D)` に対して、伝達関数\n行列 `G(λ)` のハンケルノルム `hanorm =` $\\small ||G(\\lambda)||_H$ とシステムの最小実現のハンケル特異値のベクトル `hs` を計算します。\n\n非最小システムの場合、ペア `(A,E)` の制御不能および観測不能な有限および無限の固有値と\n非動的モードは最小実現技術を使用して排除されます。\n実施された削減におけるランクの決定は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づき、\n`fast = false` の場合はより信頼性の高いSVD分解に基づきます。\n\nキーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ、\n`A`、`B`、`C`、`D` の非ゼロ要素の絶対許容誤差、\n`E` の非ゼロ要素の絶対許容誤差、\nおよび `A`、`B`、`C`、`D` および `E` の非ゼロ要素の相対許容誤差を指定します。\nデフォルトの相対許容誤差は `n*ϵ`であり、ここで`ϵ`は作業用マシンエプシロンであり、\n`n`はシステム`sys`の次数です。キーワード引数`atol`を使用して、\n同時に`atol1 = atol`および`atol2 = atol`を設定できます。\n"), nothing, Dict{Symbol, Any}(:typesig => Union{Tuple{DescriptorSystems.DescriptorStateSpace{T, ET, MT} where {ET<:Union{LinearAlgebra.UniformScaling{Bool}, AbstractMatrix{T}}, MT<:AbstractMatrix{T}}}, Tuple{T}} where T, :module => DescriptorSystems, :linenumber => 466, :binding => DescriptorSystems.ghanorm, :path => "/home/terasaki/.julia/packages/DescriptorSystems/7S3aT/src/analysis.jl"))```
