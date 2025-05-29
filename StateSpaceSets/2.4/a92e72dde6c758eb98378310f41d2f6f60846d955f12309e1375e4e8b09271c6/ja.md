```
StateSpaceSet{D, T, V} <: AbstractVector{V}
```

状態空間内の集合のための専用インターフェースです。これは、長さ `D` の**同じサイズの点の順序付きコンテナ**であり、要素の型は `T` で、型 `V` のベクターで表されます。通常、`V` は `SVector{D,T}` または `Vector{T}` であり、データは常に内部的に `Vector{V}` として保存されます。`SSSet` は `StateSpaceSet` のエイリアスです。

基礎となる `Vector{V}` は `vec(ssset)` で取得できますが、`StateSpaceSet` は `AbstractVector` をサブタイプ化し、そのインターフェースを拡張しているため、ほとんど必要ありません。`StateSpaceSet` は `append!`、`push!`、`hcat`、`eachrow` などのほぼすべての妥当なベクター操作もサポートしています。反復処理を行うと、含まれている点を反復します。

## 構築

`StateSpaceSet` の構築は、次の3つの方法で行われます。

1. 状態空間セットの各個別の**列**を `Vector{<:Real}` として与える: `StateSpaceSet(x, y, z, ...)`。
2. 行が状態空間の点である行列を与える: `StateSpaceSet(m)`。
3. ベクターのベクター（状態空間の点）を直接与える: `StateSpaceSet(v_of_v)`。

すべてのコンストラクタは、`V`（内部ベクターの型）を設定するキーワード `container` を許可します。現時点では、オプションは `SVector`、`MVector`、または `Vector` のみであり、デフォルトでは `SVector` が使用されます。

## インデックスの説明

1つのインデックスでインデックス指定された場合、`StateSpaceSet` はそのカプセル化されたベクターとまったく同じように動作します。すなわち、ベクターのベクター（状態空間の点）です。2つのインデックスでインデックス指定された場合、各行が点である行列のように動作します。

以下では、`i, j` を整数、`typeof(X) <: AbstractStateSpaceSet` とし、`v1, v2` を `<: AbstractVector{Int}` とします（`v1, v2` は範囲でも構いません。パフォーマンスの利点のために `v2` を `SVector{Int}` にします）。

  * `X[i] == X[i, :]` は `i` 番目の点を返します（`SVector` を返します）
  * `X[v1] == X[v1, :]` は、これらのインデックスにある点を持つ `StateSpaceSet` を返します。
  * `X[:, j]` は `j` 番目の変数の時系列（またはコレクション）を `Vector` として返します
  * `X[v1, v2], X[:, v2]` は適切なエントリを持つ `StateSpaceSet` を返します（最初のインデックスは「時間」/点インデックス、2番目は変数です）
  * `X[i, j]` は `i` 番目の時点での `j` 番目の変数の値です

`Matrix(ssset)` または `StateSpaceSet(matrix)` を使用して変換します。`matrix` の各*列*が1つの変数であると仮定します。さまざまな時系列ベクター `x, y, z, ...` がある場合は、`StateSpaceSet(x, y, z, ...)` のように渡します。`columns(dataset)` を使用して逆に取得できます。すなわち、データセットのすべての列をタプルとして取得します。
