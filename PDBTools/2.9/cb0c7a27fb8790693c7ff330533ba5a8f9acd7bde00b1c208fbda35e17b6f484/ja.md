```
closest(x,y)
```

二つの原子のセット間の最小距離を計算し、原子のインデックスとその距離を返します。原子のベクトルまたは座標のベクトルの両方を入力として使用できます。

### 例

```julia-repl
julia> model = wget("1BSX");

julia> protein = select(model,"protein");

julia> ligand = select(model,"resname T3");

julia> closest(ligand,protein)
(43, 3684, 2.7775834820937417)

julia> ligand[43]
    4037   O1      T3     B        2      512  -22.568   81.625    3.159 36.59  1.00     1       -      4041

julia> closest(ligand[43],protein)
(1, 3684, 2.7775834820937417)

julia> x = coor(protein)
3994-element Vector{SVector{3, Float64}}:
 [52.884, 24.022, 35.587]
 [52.916, 24.598, 36.993]
 ⋮
 [-46.887, 86.925, 13.235]
 [-47.164, 83.593, 15.25]

julia> closest(ligand,x)
(43, 3684, 2.7775834820937417)

```
