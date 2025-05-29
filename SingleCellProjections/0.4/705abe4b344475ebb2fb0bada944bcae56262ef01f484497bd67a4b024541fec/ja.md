```
project(data::DataMatrix, base::DataMatrix, args...; from=nothing, kwargs...)
```

`data`を`base`に投影し、`base`からProjectionModelsを1つずつ適用します。

`data`にはすでにいくつかのモデルが適用されている可能性があるため、`project`は`base`からどのモデルを使用するかを判断しようとします。具体的な例については以下の「例」を参照してください。以下はより技術的な概要です。

`base`データマトリックスに4つのモデルがあるとします：

```
base: A -> B -> C -> D
```

新しい`data`（通常はカウント）を与えられた場合、すべての4つのモデルを適用して得られる結果`proj`を`base`に投影できます：

```
data:
proj: A -> B -> C -> D
```

`data`にすでにいくつかのモデルが適用されている場合（例えば、上記のAとBにすでに投影されている場合）、`project`は`data`の最後のモデル（この場合はB）を`base`のモデルリストの中で探し、その後のモデル（この場合はCとD）だけを適用します。

```
data: A -> B
proj: A -> B -> C -> D
```

`from`キーワード引数を使用して、適用するモデルを正確に指定することも可能です。（`from`のモデルは`base`のモデルの接頭辞でなければならず、言い換えれば、`base`は`from`に追加の操作を適用することによって作成されました。）

```
data: X
base: A -> B -> C -> D
from: A -> B
proj: X -> C -> D
```

`data`の最後のモデルが`base`に存在しない場合、`from`キーワード引数を使用する必要があることに注意してください。なぜなら、`project`はどのモデルを適用するのが理にかなっているかを自分で判断できないからです。

# 例

まず、カウントを読み込み、SCTransformを行い、正規化し、SVDを計算し、最後にフォースレイアウトを計算することで「ベース」を構築します：

```julia
julia> fp = ["GSE164378_RNA_ADT_3P_P1.h5", "GSE164378_RNA_ADT_3P_P2.h5"];
julia> counts = load_counts(fp; sample_names=["P1","P2"]);
julia> transformed = sctransform(counts);
julia> normalized = normalize_matrix(transformed);
julia> reduced = svd(normalized; nsv=10);
julia> fl = force_layout(reduced; ndim=3, k=100)
  DataMatrix (3 variables and 35340 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform
```

最後の行が`fl`の作成に使用されたすべての`ProjectionModels`をリストしていることに注意してください。

次に、投影のためにさらにサンプルを読み込みます：

```julia
julia> fp2 = ["GSE164378_RNA_ADT_3P_P5.h5", "GSE164378_RNA_ADT_3P_P6.h5"];
julia> counts2 = load_counts(fp2; sample_names=["P5","P6"]);
```

新しく読み込んだ`counts2`を「ベース」フォースレイアウト`fl`に投影するのは簡単です：

```julia
julia> project(counts2, fl)
DataMatrix (3 variables and 42553 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform
```

中間結果にアクセスするために、2ステップ以上で投影することもできます：

```julia
julia> reduced2 = project(counts2, reduced)
DataMatrix (20239 variables and 42553 observations)
  SVD (10 dimensions)
  Variables: id, feature_type, name, genome, read, pattern, sequence, logGeneMean, outlier, beta0, ...
  Observations: id, sampleName, barcode
  Models: SVDModel(nsv=10), Normalization, SCTransform

julia> project(reduced2, fl)
DataMatrix (3 variables and 42553 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform
```

投影したいDataMatrixが変更された場合、`from`キーワード引数を使用して`project`にどのモデルを使用するかを伝える必要があります：

```julia
julia> filtered = counts2[:,1:10:end]
DataMatrix (33766 variables and 4256 observations)
  SparseArrays.SparseMatrixCSC{Int64, Int32}
  Variables: id, feature_type, name, genome, read, pattern, sequence
  Observations: id, sampleName, barcode
  Models: FilterModel(:, 1:10:42551)

julia> reduced2b = project(filtered2, reduced; from=counts)
DataMatrix (20239 variables and 4256 observations)
  SVD (10 dimensions)
  Variables: id, feature_type, name, genome, read, pattern, sequence, logGeneMean, outlier, beta0, ...
  Observations: id, sampleName, barcode
  Models: SVDModel(nsv=10), Normalization, SCTransform, Filter
```

その後、`from`を指定せずに続行することが可能です：

```julia
julia> project(reduced2b, fl)
DataMatrix (3 variables and 4256 observations)
  Matrix{Float64}
  Variables: id
  Observations: id, sampleName, barcode
  Models: NearestNeighborModel(base="force_layout", k=10), SVD, Normalization, SCTransform, Filter
```
