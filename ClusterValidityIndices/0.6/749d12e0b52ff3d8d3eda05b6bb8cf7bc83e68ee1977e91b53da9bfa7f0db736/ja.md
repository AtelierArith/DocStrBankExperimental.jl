`ClusterValidityIndices.jl`のメインモジュールは、教師なし学習のためのメトリックを提供するJuliaパッケージです。

このモジュールは、`ClusterValidityIndices.jl`パッケージで使用されるすべてのCVIモジュール、オプション、およびユーティリティをエクスポートします。完全な使用法については、公式ガイドを参照してください: https://ap6yc.github.io/ClusterValidityIndices.jl/dev/man/guide/.

# 基本的な使い方

スクリプトでパッケージをインストールしてインポートするには、次のようにします。

```julia
using Pkg
Pkg.add("ClusterValidityIndices")
using ClusterValidityIndices
```

次に、空の引数コンストラクタでCVIオブジェクトを作成します。

```julia
my_cvi = DB()
```

そして、`get_cvi!`（バッチ）または`get_icvi!`（インクリメンタル）を使用して基準値を取得します。

```julia
# クラスタリングプロセスからいくつかの特徴とラベルをロードする
features, labels = get_some_clustering_data()

# バッチ基準値
criterion_value = get_cvi!(my_cvi, features, labels)

# インクリメンタル基準値
criterion_values = zeros(length(labels))
for ix in eachindex(labels)
    criterion_values[ix] = get_icvi!(my_cvi, features[:, ix], labels[ix])
end
```

# インポート

次の名前は、パッケージによって依存関係としてインポートされます：

  * `Base`
  * `Core`
  * `DocStringExtensions`
  * `ElasticArrays`
  * `LinearAlgebra`
  * `NumericalTypeAliases`
  * `Pkg`

# エクスポート

次の名前はエクスポートされ、パッケージを`using`したときに利用可能です：

  * [`CH`](@ref)
  * [`CLUSTERVALIDITYINDICES_VERSION`](@ref)
  * [`CVI`](@ref)
  * [`CVI_MODULES`](@ref)
  * [`DB`](@ref)
  * [`GD43`](@ref)
  * [`GD53`](@ref)
  * [`PS`](@ref)
  * [`WB`](@ref)
  * [`XB`](@ref)
  * [`cSIL`](@ref)
  * [`get_cvi!`](@ref)
  * [`rCIP`](@ref)
