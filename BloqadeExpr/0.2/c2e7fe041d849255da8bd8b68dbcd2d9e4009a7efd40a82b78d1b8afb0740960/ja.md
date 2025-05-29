```
rydberg_h_3(atoms; [C=2π * 862690 * MHz*µm^6, 
    Ω_hf = nothing, ϕ_hf = nothing, Δ_hf = nothing, 
    Ω_r = nothing, ϕ_r = nothing, Δ_r = nothing])
```

3レベルのライデンバーグハミルトニアンを作成します

$$
\sum_{i<j} \frac{C}{|x_i - x_j|^6} n^r_i n^r_j + 
\sum_{i} \left[\frac{Ω^{\mathrm{hf}}}{2} (e^{iϕ^\mathrm{hf}}|0⟩⟨1| + e^{-iϕ^\mathrm{hf}}|1⟩⟨0|) - Δ^{\mathrm{hf}} n^{1}_i + 
\frac{Ω^{\mathrm{r}}}{2} (e^{iϕ^\mathrm{r}}|1⟩⟨r| + e^{-iϕ^\mathrm{r}}|r⟩⟨1|) - (Δ^{\mathrm{hf}} + Δ^{\mathrm{r}}) n^{\mathrm{r}}_i \right]
$$

の省略形は

```julia
RydInteract(C, atoms; nlevel = 3) + 
    SumOfXPhase_01(length(atoms), Ω_hf/2, ϕ_hf) - SumOfN(length(atoms), Δ_hf) +
    SumOfXPhase_1r(length(atoms), Ω_r/2, ϕ_r) - SumOfN(length(atoms), Δ_r + Δ_hf)
```
