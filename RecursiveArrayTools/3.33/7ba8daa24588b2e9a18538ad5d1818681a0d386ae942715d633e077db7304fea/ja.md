```julia
VectorOfArray(u::AbstractVector)
```

`VectorOfArray`は、基盤となるデータ構造が`Vector{AbstractArray{T}}`（しかし、具体的には型付けされていることを期待します！）である配列です。このようなデータ構造のラッパーは、高次元ベクトルのように遅延的に振る舞うことを可能にし、さまざまな形式に簡単に変換できます。インデックス構造は次のようになります：

```julia
A.u[i] # ベクトルの配列のi番目の配列を返します
A[j, i] # i番目の配列のj番目の成分を返します
A[j1, ..., jN, i] # i番目の配列の(j1,...,jN)成分を返します
```

これは、列がベクトルからの配列である列優先の行列として表現されます。`AbstractArray`インターフェースが実装されており、`copy`、`push`、`append!`などの関数にアクセスでき、適切に動作します。注意すべき点は次のとおりです：

  * 長さはベクトルの数、または`length(A.u)`であり、ここで`u`は配列のベクトルです。
  * イテレーションは線形インデックスに従い、ベクトルを走査します。

さらに、`convert(Array,VA::AbstractVectorOfArray)`関数が提供されており、`VectorOfArray`を行列/テンソルに変換します。また、`vecarr_to_vectors(VA::AbstractVectorOfArray)`は、各成分の系列のベクトルを返します。つまり、各`i`に対して`A[i,:]`です。プロットレシピも提供されており、`A[i,:]`系列をプロットします。

多次元配列から構築された`VectorOfArray`もサポートされています。

```julia
VectorOfArray(u::AbstractArray{AT}) where {T, N, AT <: AbstractArray{T, N}}
```

ここで、`IndexStyle(typeof(u)) isa IndexLinear`です。
