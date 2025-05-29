```
productstatemps(physdims::Dims, Dmax=1; state=:Vacuum, mpsorthog=:Right)
```

ローカルヒルベルト空間の次元が `physdims` で与えられる積状態を表すMPSを返します。

デフォルトでは、すべてのボンド次元は1になります。なぜなら、状態が積状態だからです。しかし、積状態をより大きなボンド次元の多様体に埋め込むために、`Dmax` を適宜設定することができます。

MPSサイトの個々の状態は、`state` を列ベクトルのリストに設定することで提供できます。`state=:Vacuum` を設定すると、真空状態のMPSが生成されます（この場合、各サイトの状態は最初の行に1があり、他の行はゼロの列ベクトルで表されます）。`state=:FullOccupy` を設定すると、各サイトが完全に占有されたMPSが生成されます（つまり、最終行に1があり、他の行はゼロの列ベクトルです）。

引数 `mpsorthog` は、結果のMPSのゲージを設定するために使用できます。

# 例

```julia-repl
julia> ψ = unitcol(1,2); d = 6; N = 30; α = 0.1; Δ = 0.0; ω0 = 0.2; s = 1

julia> cpars = chaincoeffs_ohmic(N, α, s)

julia> H = spinbosonmpo(ω0, Δ, d, N, cpars)

julia> A = productstatemps(physdims(H), state=[ψ, fill(unitcol(1,d), N)...]) # MPS表現の |ψ>|Vacuum>
```
