```
update_adjacency!(a,f_update)
```

隣接オブジェクトのデータを更新する関数です。`a` は `MatrixAdjacency` または `GraphAdjacency` でなければならず、`f_update` は `f_update = x->update_function!(x)` の形式でなければなりません。

# 例

julia> using NetworkLearning, LightGraphs

julia> A = [0 1 0; 1 0 0; 0 0 0];

julia> Am = adjacency(A) 行列隣接、3 観測

julia> update*function!(X,x,y) = begin          X[x,y] += 1          X[y,x] += 1          return X        end update*function! (一般的な関数で 2 つのメソッド)

julia> f*update(x,y) = X->update*function!(X,x,y) f_update (一般的な関数で 1 つのメソッド)

julia> for i in 1:3          update*adjacency!(Am, f*update(1,3)) # 関数を 3 回呼び出す        end

julia> adjacency_matrix(Am) 3×3 Array{Int64,2}:  0  1  3  1  0  0  3  0  0
