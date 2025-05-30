```
match_template!(dest, source, template, alg::Algorithm)
```

テンプレートマッチングを実行し、結果を事前に割り当てられた宛先配列に書き込みます。

`match_template`のインプレース対応版で、テンプレートマッチング操作を実行し、ユーザーが渡した事前に割り当てられた配列`dest`に結果を保存するように設計されています。これによりメモリの割り当てが減少し、複数のテンプレートマッチング操作を行う際により効率的になる可能性があります。指定されたアルゴリズムを使用してテンプレートをソース画像と比較し、多次元配列や画像のセットに適しています。

さらなるドキュメントについては[`match_template`](@ref)を参照してください。

# 引数

  * `dest`: 結果が保存される事前に割り当てられた宛先配列。
  * `source`: 検索対象のソース配列。
  * `template`: 検索するテンプレート配列。
  * `alg::Algorithm`: 類似度を計算するためのアルゴリズム。

# 戻り値

計算された類似度メトリックをソース画像上のテンプレートの各位置に含む最初の引数`dest`を返します。

`source`配列の次元は、テンプレート配列の次元以上である必要があります。ソースがサイズ`(S_1, S_2, ...)`で、`template`が`(T_1, T_2, ...)`の場合、`dest`は次元`(S_1-T_1+1, S_2-T_2+1, ...)`で事前に割り当てられている必要があり、ソース上のテンプレートの各可能な位置に対する類似度メトリックを表します。

マッチングのアルゴリズムは、`alg`パラメータとして次の構造体のいずれかのインスタンスを渡すことで選択されます: [`SquareDiff`](@ref), [`NormalizedSquareDiff`](@ref), [`CrossCorrelation`](@ref), [`NormalizedCrossCorrelation`](@ref), [`CorrelationCoeff`](@ref), または[`NormalizedCorrelationCoeff`](@ref)。

# 例

```julia
source = rand(100, 100)
template = rand(10, 10)
dest = Array{Float64}(undef, 91, 91)
match_template!(dest, source, template, CrossCorrelation())

dest = Array{Float64}(undef, 100, 100)
match_template!(dest, source, template, CrossCorrelation()) # 失敗します
```

この関数の不変版については、[`match_template`](@ref)も参照してください。
