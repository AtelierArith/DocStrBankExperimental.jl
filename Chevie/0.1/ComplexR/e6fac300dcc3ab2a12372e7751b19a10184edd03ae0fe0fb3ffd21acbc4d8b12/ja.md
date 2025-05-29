`hyperplane_orbits(W::ComplexReflectionGroup)`

は、反射群 `W` の各ハイパープレーン軌道に対して1つの名前付きタプルのリストを返します。もし `o` がそのような軌道の名前付きタプルであり、`s` がその軌道にハイパープレーンが含まれる `gens(W)` の最初の要素である場合、以下のフィールドが含まれます。

`.s`:     `gens(W)` における `s` のインデックス

`.order`: `s` の順序

`.cl_s`:  `i` が `1:order-1` の範囲のとき、`position_class(W,W(s)^i)`

`.N_s`:    ハイパープレーン軌道のサイズ

`.det_s`:  `i` が `1:order-1` の範囲のとき、`detₛⁱ` の `CharTable(W)` における位置、ここで `detₛ` は `s` に対して `det(reflrep(W,s))` の値を取り、非共役反射に対しては `1` の値を取る線形キャラクタです。

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> hyperplane_orbits(W)
2-element Vector{@NamedTuple{s::Int64, cl_s::Vector{Int64}, order::Int64, N_s::Int64, det_s::Vector{Int64}}}:
 (s = 1, cl_s = [2], order = 2, N_s = 2, det_s = [5])
 (s = 2, cl_s = [4], order = 2, N_s = 2, det_s = [1])
```
