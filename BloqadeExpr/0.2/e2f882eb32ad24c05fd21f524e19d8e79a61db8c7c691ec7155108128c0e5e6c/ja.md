```
rydberg_h(atoms; [C=2π * 862690 * MHz*µm^6], Ω[, ϕ, Δ])
```

Rydberg ハミルトニアンを作成します

$$
∑ \frac{C}{|x_i - x_j|^6} n_i n_j + \frac{Ω}{2} σ_x - Δ σ_n
$$

の省略形は

```julia
RydInteract(C, atoms) + SumOfXPhase(length(atoms), Ω, ϕ) - SumOfN(length(atoms), Δ)
```

# 引数

  * `atoms`: 原子の位置のコレクション。

# キーワード引数

  * `C`: オプション、デフォルト単位は `MHz*µm^6`、相互作用パラメータ、詳細は [`RydInteract`](@ref) を参照。
  * `Ω`: オプション、デフォルト単位は `MHz`、ラビ周波数、2で割る、詳細は [`SumOfX`](@ref) を参照。
  * `Δ`: オプション、デフォルト単位は `MHz`、デチューニングパラメータ、詳細は [`SumOfN`](@ref) を参照。
  * `ϕ`: オプション、単位はなく、位相、詳細は [`SumOfXPhase`](@ref) を参照。

!!! tips
    Rydberg ハミルトニアンではラビ周波数が2で割られますが、[`SumOfX`](@ref) や [`SumOfXPhase`](@ref) を直接構築する場合はそうではありません。


!!! tips
    ハミルトニアンのパラメータにはハードウェアに合わせた独自のデフォルト単位があります。明示的に単位を指定するには [`Unitful.jl`](https://github.com/PainterQubits/Unitful.jl) を使用できます。単位が明示的に指定されている場合、デフォルト単位に自動的に変換されます。


# 例

```julia-repl
julia> using Bloqade

julia> atoms = [(1, ), (2, ), (3, ), (4, )]
4-element Vector{Tuple{Int64}}:
 (1,)
 (2,)
 (3,)
 (4,)

julia> rydberg_h(atoms)
∑ 5.42e6/|x_i-x_j|^6 n_i n_j
```

```julia-repl
julia> rydberg_h(atoms; Ω=0.1)
nqubits: 4
+
├─ ∑ 5.42e6/|x_i-x_j|^6 n_i n_j
└─ 0.05 ⋅ ∑ σ^x_i
```
