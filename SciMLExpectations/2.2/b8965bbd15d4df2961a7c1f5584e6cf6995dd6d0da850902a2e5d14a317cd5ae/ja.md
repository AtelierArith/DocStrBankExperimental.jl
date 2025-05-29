```julia
ProcessNoiseSystemMap(prob, n, args...; kwargs...)
```

与えられた `prob::SDEProblem` のシステムソリューションマップの表現。`args` と `kwargs` は方程式ソルバーに転送されます。`n` はプロセスノイズのコサンビ–カルフネン–ローヴ表現における項の数です。
