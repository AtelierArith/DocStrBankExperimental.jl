```
match_template(source, template, alg::Algorithm)
```

指定されたアルゴリズムを使用して、ソース画像とテンプレートの間でテンプレートマッチングを実行します。

`alg`パラメータで指定されたアルゴリズムを使用して、テンプレートをソース画像と比較します。これは、2次元以上の配列で動作するように設計されており、多次元配列や画像のセットに適しています。この関数は、ソース配列のすべての可能な位置でテンプレートをスライドさせ、各位置で類似度メトリックを計算します。

# 引数

  * `source`: 検索対象のソース配列。
  * `template`: 検索するテンプレート配列。
  * `alg::Algorithm`: 類似度メトリックを計算するために使用するアルゴリズム。

`source`配列の次元は、`template`配列の次元以上である必要があります。`source`がサイズ`(S_1, S_2, ...)`で、`template`が`(T_1, T_2, ...)`の場合、結果のマッチ配列のサイズは`(S_1-T_1+1, S_2-T_2+1, ...)`となり、ソース上のテンプレートの各可能な位置に対する類似度メトリックを表します。

マッチングのアルゴリズムは、次の構造体のいずれかのインスタンスを`alg`パラメータとして渡すことによって選択されます: [`SquareDiff`](@ref), [`NormalizedSquareDiff`](@ref), [`CrossCorrelation`](@ref), [`NormalizedCrossCorrelation`](@ref), [`CorrelationCoeff`](@ref), または [`NormalizedCorrelationCoeff`](@ref)。

# 戻り値

入力配列と同じ次元数の配列を返し、ソース画像上のテンプレートの各位置で計算された類似度メトリックを含みます。

# 例

```julia
source = rand(100, 100)
template = rand(10, 10)
result = match_template(source, template, CrossCorrelation())
```

```jldoctest
source = rand(100, 100)
template = source[10:15, 20:30]
result = match_template(source, template, SquareDiff())
argmin(result)

# 出力
CartesianIndex(10, 20)
```

```jldoctest
source = rand(100, 100)
template = source[10:15, 20:30]
result = match_template(source, template, CorrelationCoeff())
argmax(result)

# 出力
CartesianIndex(10, 20)
```

結果を事前に確保された配列に書き込むこの関数のバージョンについては、[`match_template!`](@ref)も参照してください。
