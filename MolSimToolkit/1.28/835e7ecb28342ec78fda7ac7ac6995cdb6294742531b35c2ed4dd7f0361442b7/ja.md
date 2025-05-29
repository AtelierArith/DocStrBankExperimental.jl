```
ss_mean(ssmap::AbstractMatrix{<:Integer}; class, dims=nothing)
```

与えられた二次構造マップに基づいて、軌道の平均二次構造クラスの内容を計算します。

考慮すべき二次構造クラスは、`class`キーワード引数によって定義されなければなりません。

`class`は文字列、文字、整数、または値のセットのいずれかであり、考慮される二次構造のクラスを設定します。たとえば、`alpha helix`の場合は「H」を使用します。また、`class=["H", "E"]`のようにクラスのベクターにすることもできます。

平均は、`dims`キーワード引数を設定することによって、残基に沿って（デフォルト）またはフレームに沿って計算できます。

  * `dims=nothing`（デフォルト）は、全体の行列の`ss_class`の平均出現を計算します。
  * `dims=1`は、各残基についてフレームに沿った`ss_class`の平均出現を計算します。
  * `dims=2`は、各フレームについて残基に沿った`ss_class`の平均出現を計算します。

クラスは、ProteinSecondaryStructures.jlパッケージのドキュメントで見つけることができます。

## 例

```jldoctest ;filter = r"(\d*)\.(\d{4})\d+" => s"\1.\2***"
julia> using MolSimToolkit, MolSimToolkit.Testing

julia> simulation = Simulation(Testing.namd_pdb, Testing.namd_traj);

julia> ssmap = ss_map(simulation; # 5フレーム 
                   selection="residue >= 30 and residue <= 35", # 6残基
                   show_progress=false
               );

julia> ss_mean(ssmap; class="C")
0.23333333333333334

julia> ss_mean(ssmap; class="C", dims=1) # 残基ごとの平均コイル含量
5-element Vector{Float64}:
 0.16666666666666666
 0.5
 0.16666666666666666
 0.16666666666666666
 0.16666666666666666 

julia> ss_mean(ssmap; class="C", dims=2) # フレームごとの平均コイル含量
6-element Vector{Float64}:
 0.2
 0.2
 0.0
 0.0
 0.0
 1.0

julia> ss_mean(ssmap; class=["C", "T"]) # コイルまたはターンの平均
0.9

```
