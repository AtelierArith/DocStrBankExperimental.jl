```
struct KrylovEvolution
KrylovEvolution(reg::AbstractRegister, clocks, h; kw...)
```

Krylovサブスペース法を使用して時間発展を記述する`KrylovEvolution`オブジェクトを作成します。

# 引数

  * `reg`: レジスタで、`AbstractRegister`のサブタイプである必要があります。
  * `clocks`: 各ステップでのこの時間発展のクロック。
  * `h`: ハミルトニアンの式。

# キーワード引数

  * `progress`: 進行状況バーを表示する、デフォルトは`false`。
  * `progress_name`: 進行状況バーの名前、デフォルトは`"emulating"`。
  * `normalize_step`: `normalize_step`ごとに状態を正規化します。
  * `normalize_finally`: 発展の最後に状態を正規化するかどうか、デフォルトは`true`。
  * `tol`: Krylov法の許容誤差、デフォルトは`1e-7`

# 例

以下は、[`emulate!`](@ref)を介して`KrylovEvolution`を使用する最も簡単な方法です。より高度な使用法については、ドキュメンテーションページ[Emulation](@ref emulation)を参照してください。

```jldoctest
julia> using Bloqade

julia> r = zero_state(5)
ArrayReg{2, ComplexF64, Array...}
    active qudits: 5/5
    nlevel: 2

julia> atoms = [(i, ) for i in 1:5]
5-element Vector{Tuple{Int64}}:
 (1,)
 (2,)
 (3,)
 (4,)
 (5,)

julia> h = rydberg_h(atoms; Ω=sin)
nqubits: 5
+
├─ [+] ∑ 5.42e6/|x_i-x_j|^6 n_i n_j
└─ [+] Ω(t) ⋅ ∑ σ^x_i


julia> prob = KrylovEvolution(r, 0.0:1e-2:0.1, h);

julia> emulate!(prob); # run the emulation
```
