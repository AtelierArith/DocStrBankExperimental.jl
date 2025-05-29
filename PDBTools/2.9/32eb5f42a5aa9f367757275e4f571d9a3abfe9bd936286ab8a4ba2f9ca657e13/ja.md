```
distance(x,y)
```

二つの原子のセット間、原子と原子のセット間、または単に二つの原子間の最小距離、または座標または座標のセットからの距離を計算します。

入力は、`Atom`のベクトル、3Dベクトル、または座標の3Dベクトルのベクトルである場合があります。これは、`coor`関数によって出力される例です。

### 例

```julia-repl
julia> model = wget("1BSX");

julia> protein = select(model,"protein");

julia> ligand = select(model,"resname T3");

julia> distance(protein,ligand)
2.7775834820937417

julia> distance(protein[1],ligand[3])
36.453551075306784

julia> distance(coor(ligand),protein)
2.7775834820937417

```
