```
SparseMatrixExp{N}
```

スパース行列の行列指数関数 $\exp(M)$ を表す型。

### フィールド

  * `M` – スパース正方行列

### 例

例えば、次のような $100 × 100$ のランダムスパース行列を考え、占有確率を $0.1$ とします：

```jldoctest SparseMatrixExp_constructor
julia> using SparseArrays

julia> A = sprandn(100, 100, 0.1);

julia> using ExponentialUtilities

julia> E = SparseMatrixExp(A);

julia> size(E)
(100, 100)
```

ここで `E` は $\exp(A)$ の遅延表現です。`E` を使って計算するには、`get_row` と `get_column`、それぞれ `get_rows` と `get_columns` を使用します。これらの関数は行ベクトルと列ベクトル（または行列）を返します。例えば：

```jldoctest SparseMatrixExp_constructor
julia> get_row(E, 10);  # E[10, :] を計算

julia> get_column(E, 10);  # E[:, 10] を計算

julia> get_rows(E, [10]);  # get_row(E, 10) と同じですが、1x100 行列を返します

julia> get_columns(E, [10]);  # get_column(E, 10) と同じですが、100x1 行列を返します
```

### 注意事項

この型は大きくてスパースな行列での使用のために提供されています。ベクトルに対する指数行列作用の評価は、[ExponentialUtilities](https://github.com/SciML/ExponentialUtilities.jl) や [Expokit](https://github.com/acroy/Expokit.jl) などの外部パッケージに依存しています。したがって、`SparseMatrixExp` の機能にアクセスするには、そのようなオプショナルな依存関係をインストールしてロードする必要があります。
