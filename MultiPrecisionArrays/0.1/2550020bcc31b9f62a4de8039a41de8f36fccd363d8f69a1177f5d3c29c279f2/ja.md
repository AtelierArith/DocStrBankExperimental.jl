hlu!(A::AbstractMatrix{T}) where {T} AのLU因子分解を返します

C. T. Kelley, 2023

この関数は、次の一部であるgeneric_lufact!のハックです。

https://github.com/JuliaLang/julia/blob/master/stdlib/LinearAlgebra/src/lu.jl

私はコードをFloat16専用に「修正」し、ピボットをMaxRowのみに固定しました。

因子分解では、重要なループをFLoops.@floopでスレッド化し、内側のループに@simdを入れただけです。より大きな問題（n > 128）では、これらの変更により、私のMac M2 Proの8つのパフォーマンスコアで2-10倍のスピードアップを得ることができました。私は満足しています。
