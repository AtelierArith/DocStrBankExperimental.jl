```
lc, mvf = example_clorenz()
```

図3に示されたKaczynski、Mrozek、WannerによるJCD 2016論文の例のための単体複体と多ベクトル場を作成します。

この関数は、有限体GF(2)上のLefschetz複体`lc`と多ベクトル場`mvf`を返します。

# 例

```jldoctest
julia> lc, mvf = example_clorenz();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0   1]
[0   0   0   0   0]
[0   0   0   0   1]
[0   0   0   0   0]
[0   0   0   0   0]

julia> print(cm.labels)
["i", "ip", "g", "gm", "bc"]

julia> ms, ps = morse_sets(lc, mvf, poset=true);

julia> [conley_index(lc, mset) for mset in ms]
4-element Vector{Vector{Int64}}:
 [1, 1, 0]
 [1, 1, 0]
 [0, 1, 0]
 [0, 0, 0]

julia> ps
4×4 Matrix{Bool}:
 0  0  1  0
 0  0  1  0
 0  0  0  1
 0  0  0  0
```
