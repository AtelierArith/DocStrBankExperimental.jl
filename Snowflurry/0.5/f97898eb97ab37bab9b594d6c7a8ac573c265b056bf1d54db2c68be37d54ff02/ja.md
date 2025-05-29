```
wigner(ρ::AbstractOperator, p::Real, q::Real)
```

密度行列 `ρ` のウィグナー関数を点 (`p`,`q`) で計算します。

```jldoctest
julia> alpha = 0.25;

julia> hspace_size = 8;

julia> Ψ = coherent(alpha, hspace_size);

julia> prob = wigner(ket2dm(Ψ), 0, 0);

julia> @printf "prob: %.6f" prob
prob: 0.561815
```
