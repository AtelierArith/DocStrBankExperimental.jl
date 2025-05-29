`Category{TO,TM}` は、オブジェクトが `TO` 型で、マップが `TM` 型の有限カテゴリの型です。これは、2つのフィールドを持つ `struct` として表現されます：

  * `obj::Vector{TO}` オブジェクト
  * `atoms::Vector{Vector{Pair{TM,Int}}}` カテゴリの原子（生成子）を表すベクトル。これは `atoms[i]` が `obj[i]` から `obj[j]` へのマップ `m` を表すペア `m=>j` の `Vector` であるように構成されています。もし `TM` 型のジュリアオブジェクトがモノイドに属する場合、一般的なマップは `(i,m,j)` という三重項として表現でき、ここで `m` は `obj[i]` から `obj[j]` へのマップを表す `TM` 型です。

カテゴリは `:graph` io プロパティを指定することでグラフィカルに表示されます：

```julia-rep1
julia> W=coxsym(4);M=BraidMonoid(W)
BraidMonoid(𝔖 ₄)

julia> xprint(conjcat(M(1,1,2,2,3));graph=true)
category with 4 objects and 8 generating maps
      1232       12       213       213       213       32 
213.32―――➔ 12.213―➔ 213.12――➔ 12.213――➔ 213.32――➔ 32.213―➔ 213.32
      1321       213 
213.12―――➔ 32.213――➔ 213.12
```
