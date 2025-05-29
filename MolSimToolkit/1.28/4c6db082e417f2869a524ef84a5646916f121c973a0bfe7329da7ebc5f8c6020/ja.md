```
distances(simulation, indices1::AbstractVector{<:Integer}, indices2::AbstractVector{<:Integer})
distances(simulation, selection1::AbstractVector{<:PDBTools.Atom}, selection2::AbstractVector{<:PDBTools.Atom})
```

シミュレーション内の2つの選択の質量中心間の距離を計算する関数です。

選択は、原子のインデックスであるindices1およびindices2ベクトルによって定義されるか、または`PDBTools.Atom`オブジェクトのベクトルであるselection1およびselection2ベクトルによって定義されます。

`silent=true`を使用して進行状況バーを抑制します。

# 例

```jldoctest; filter = r"([0-9]+\.[0-9]{2})[0-9]+" => s"\1***"
julia> using PDBTools

julia> using MolSimToolkit, MolSimToolkit.Testing

julia> sim = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ats = atoms(sim);

julia> i1 = findall(sel"protein and residue 1", ats); # インデックス

julia> i2 = findall(sel"protein and residue 15", ats); # インデックス

julia> distances(sim, i1, i2; silent=true)
5-element Vector{Float64}:
 23.433267858947584
 30.13791365033211
 28.48617683945202
 27.92740141686934
 23.235012287435566

julia> distances(sim, 
           filter(sel"protein and residue 1", ats), # 選択 (PDBTools.Atom)
           filter(sel"protein and residue 15", ats); # 選択 (PDBTools.Atom) 
           silent=true
       )
5-element Vector{Float64}:
 23.433267858947584
 30.13791365033211
 28.48617683945202
 27.92740141686934
 23.235012287435566
```
