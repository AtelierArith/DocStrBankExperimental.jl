```
getValue(solution::FMUSolution, vr::fmi2ValueReferenceFormat; isIndex::Bool=false)
```

ソリューションの値を返します。

# 引数

  * `solution::FMUSolution`: 特定のFMUのソリューション `value`、`success`、`state` および `events` に関する情報を含む構造体。
  * `vr::fmi2ValueReferenceFormat`: ユーザーが fmi[X]ValueReference を渡す方法のワイルドカード（デフォルト = md.valueReferences）

より詳細には: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `isIndex::Bool=false`: 引数 `isIndex` は、`vr` が与えられた fmi2ValueReferenceFormat に等しい特定のソリューション要素（"index"）であるかどうかを確認するために存在します。

# 戻り値

  * 与えられた参照の長さが1である場合、コレクション `solution.values.saveval` の各要素 u は、indices[1] で表されるインデックスの要素を選択し、それを返します。

したがって、collect() 関数はジェネレーター式を取り、選択された要素の配列を返します。

  * 参照が1つ以上与えられた場合、以前と同じプロセスが行われます。違いは、今は複数のインデックスにアクセスすることです。

# 出典

  * FMISpec2.0.2 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 プラットフォーム依存の定義 (fmi2TypesPlatform.h)
