```
nm_glob_ham(A[, hamiltonians][, weights, epsilon])
```

モラリゼーション手法のためのグローバルハミルトニアンを返します。行列 `A` は、非モラリゼーションダイナミクスを構築することを目指す有向グラフの隣接行列である必要があります。ここで、`hamiltonians` はオプションの引数で、キーが `Tuple{Int, Int}` または `Tuple{Vertex, Vertex}` の辞書です。最初のものは形状に応じてサブ行列を収集し、2番目のものは各頂点のペアに応じてそれらを収集します。デフォルトでは、すべての要素が1のサブ行列が選択されます。最後の引数は、`abs(A[i, j]) >= epsilon` である要素のみが考慮されることを示します。

*注意:* 結果行列のサブ行列は、対応する `weights` 引数によってスケーリングされます。`weights` は `A` と同じ次元の正方行列である必要があります。`weights` が提供されない場合、`weights[i,j]=A[i,j]` となり、`A[i,j]` が非ゼロで `A[j,i]` がゼロの場合、`weights[i,j]=A[j,i]` となり、`A[i,j]` が逆のシナリオの場合、`weights[i,j]=(A[i,j]+A[j,i])/2` となり、両方が非ゼロの場合はその値が使われ、そうでない場合はゼロになります。

# 例

```jldoctest; setup = :(using QSWalk)
julia> A = [ 0 1 0; 1 0 1; 0 1 0]
3×3 Array{Int64,2}:
 0  1  0
 1  0  1
 0  1  0

julia> nm_glob_ham(A) |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  1.0+0.0im  1.0+0.0im  0.0+0.0im
 1.0+0.0im  0.0+0.0im  0.0+0.0im  1.0+0.0im
 1.0+0.0im  0.0+0.0im  0.0+0.0im  1.0+0.0im
 0.0+0.0im  1.0+0.0im  1.0+0.0im  0.0+0.0im

julia> dict_deg = Dict{Tuple{Int,Int},Matrix{ComplexF64}}((1, 2) => (2+1im)*ones(1, 2), (2, 1) =>1im*ones(2, 1));

julia> nm_glob_ham(A, dict_deg) |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  2.0+1.0im  2.0+1.0im  0.0+0.0im
 2.0-1.0im  0.0+0.0im  0.0+0.0im  0.0+1.0im
 2.0-1.0im  0.0+0.0im  0.0+0.0im  0.0+1.0im
 0.0+0.0im  0.0-1.0im  0.0-1.0im  0.0+0.0im

julia> v1, v2, v3 = vlist(make_vertex_set(A))
3-element Array{Vertex,1}:
 Vertex([1])
 Vertex([2, 3])
 Vertex([4])

julia> dict_vec = Dict{Tuple{Vertex,Vertex},Matrix{ComplexF64}}((v1, v2) =>2*ones(1, 2), (v2, v3) =>[1im 2im;]');

julia> nm_glob_ham(A, dict_vec) |> Matrix
4×4 Array{Complex{Float64},2}:
 0.0+0.0im  2.0+0.0im  2.0+0.0im  0.0+0.0im
 2.0+0.0im  0.0+0.0im  0.0+0.0im  0.0-1.0im
 2.0+0.0im  0.0+0.0im  0.0+0.0im  0.0-2.0im
 0.0+0.0im  0.0+1.0im  0.0+2.0im  0.0+0.0im
```
