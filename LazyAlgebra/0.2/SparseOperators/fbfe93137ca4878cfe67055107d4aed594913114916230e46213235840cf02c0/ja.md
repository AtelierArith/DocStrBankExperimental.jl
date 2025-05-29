```
CompressedSparseOperator{F,T,M,N}
```

は `SparseOperator{T,M,N}` の抽象サブタイプであり、圧縮ストレージ形式 `F` でスパースオペレーターを実装する具体的な型によって継承されます。

形式 `F` はシンボルとして指定され、次のようになります：

  * `:COO` は *Compressed Sparse Coordinate* ストレージ形式です。この形式は最も効率的ではなく、主に以下の形式のいずれかでスパースオペレーターを構築するための中間として使用されます。
  * `:CSC` は *Compressed Sparse Column* ストレージ形式です。この形式はスパースオペレーターの随伴を適用するのに非常に効率的です。
  * `:CSR` は *Compressed Sparse Row* ストレージ形式です。この形式はスパースオペレーターを直接適用するのに非常に効率的です。

圧縮ストレージ形式 `F` のスパースオペレーターを構築（または変換）するには、次のように呼び出すことができます：

```
CompressedSparseOperator{F}(args...; kwds...)
CompressedSparseOperator{F,T}(args...; kwds...)
CompressedSparseOperator{F,T,M}(args...; kwds...)
CompressedSparseOperator{F,T,M,N}(args...; kwds...)
```

ここで、与えられたパラメータ `T`、`M` および `N` に対して、引数 `args...` とオプションのキーワード `kwds...` は、形式 `F` に対応する具体的なコンストラクタ [`SparseOperatorCOO`](@ref)、[`SparseOperatorCSC`](@ref) または [`SparseOperatorCSR`](@ref) に渡されます。

圧縮スパースオペレーター `A` をイテレータとして使用することも可能です：

```julia
for (Aij,i,j) in A # CSR と CSC では単純ですが遅い
    ...
end
```

これにより、`A` に格納されているすべてのエントリの値 `Aij` とそれぞれの行 `i` および列 `j` のインデックスを取得できます。ただし、圧縮形式に依存するストレージ順序に従ってアクセスする方が効率的です。

  * `A` が CSC 形式の場合：

    ```julia
    using LazyAlgebra.SparseMethods
    for j in each_col(A)        # 列インデックスをループ
        for k in each_off(A, j) # この列の構造的非ゼロをループ
            i   = get_row(A, k) # エントリの行インデックスを取得
            Aij = get_val(A, k) # エントリの値を取得
         end
    end
    ```
  * `A` が CSR 形式の場合：

    ```julia
    using LazyAlgebra.SparseMethods
    for i in each_row(A)        # 行インデックスをループ
        for k in each_off(A, i) # この行の構造的非ゼロをループ
            j   = get_col(A, k) # エントリの列インデックスを取得
            Aij = get_val(A, k) # エントリの値を取得
         end
    end
    ```
  * `A` が COO 形式の場合：

    ```julia
    using LazyAlgebra.SparseMethods
    for k in each_off(A)
         i   = get_row(A, k) # エントリの行インデックスを取得
         j   = get_col(A, k) # エントリの列インデックスを取得
         Aij = get_val(A, k) # エントリの値を取得
    end
    ```

低レベルのメソッド `each_row`、`each_col`、`each_off`、`get_row`、`get_col` および `get_val` は `LazyAlgebra` によって自動的にエクスポートされないため、`using LazyAlgebra.SparseMethods` の文が必要です。
