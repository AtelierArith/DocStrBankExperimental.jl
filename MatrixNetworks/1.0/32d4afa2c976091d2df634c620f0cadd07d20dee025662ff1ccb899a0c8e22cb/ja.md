# `seeded_pagerank`

PageRankは、次のように定義されたマルコフ連鎖の定常分布です。この連鎖の状態iでの挙動は次のとおりです。

  * 確率$lpha$で、現在のノードの出力隣接ノードのいずれかにランダムに遷移します（グラフに非負の重みがある場合は、重み付き確率に基づきます）。
  * 確率$1-lpha$で、テレポーテーション分布と呼ばれる分布に従ってジャンプし、ベクトル$v$によって与えられます。（標準的な場合、$v$はノード上の一様分布ですが、これはパラメータです）。
  * 出力隣接ノードがない場合は、テレポーテーション分布に従って遷移します（これは強くパーソナライズされた問題です）。

$$
v
$$

が一様ベクトルである場合、私たちはPageRank呼び出し自体と同じものを計算します。

この解は線形方程式系を満たします。この関数は、デフォルトでマシン精度に設定された`tol`の1ノルム誤差でその線形系を解決します。

解は常に確率分布です。

## 関数

  * 任意の入力に対して、Aは`A::SparseMatrixCSC{V,Int}`（ある値の型V）または`A::MatrixNetwork{V}`のいずれかであることができます。
  * `x = seeded_pagerank(A,alpha::Float64,v::Float64)`
  * `x = seeded_pagerank(A,alpha::Float64,v::Int)`
  * `x = seeded_pagerank(A,alpha::Float64,v::Set{Int})`
  * `x = seeded_pagerank(A,alpha::Float64,v::Dict{Int,Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::SparseMatrixCSC{Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::SparseVector{Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::Vector{Float64})`
  * `x = seeded_pagerank(A,alpha::Float64,v::Vector{Float64})`
  * `x = seeded_pagerank(A,alpha,v,eps::Float64)`は解の許容誤差も指定します。

## 入力

  * `A`: PageRankを計算するために使用する疎行列または行列ネットワーク。疎行列の場合、非負の値を持っている必要があり、値はアルゴリズムの一部として確率的正規化を計算するために影響を与えます。
  * `alpha`: 上記のテレポーテーションパラメータ。
  * `v`: テレポーテーション分布ベクトル。これは、単一のノードにテレポートするための整数、ノードのセットに（均等に）テレポートするためのセット、テレポーテーションに重みを付けるための辞書または疎ベクトル、または一般的な密なベクトルであることができます。
  * `tol`: 線形系を解くための許容誤差（これは誤差保証です）。

## 例

```
seeded_pagerank(A,alpha,5) 
            # ノード5へのテレポーテーションを伴う 
            # シードされたPageRankベクトルを返します 
            # マシン精度で計算されます            
```
