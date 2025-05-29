```
SpectralIndex(index::Dict{String, Any})
```

このオブジェクトは、Awesome Spectral Indices リストの特定のスペクトルインデックスとのインタラクションを可能にします。スペクトルインデックスの属性にアクセスでき、インデックス自体を計算することができます。

# 引数

  * `index::Dict{String, Any}`: 次のキーを持つ辞書：

      * `"short_name"`: スペクトルインデックスの短い名前。
      * `"long_name"`: スペクトルインデックスの長い名前または説明。
      * `"bands"`: インデックス計算に使用されるバンドまたは波長のリスト。
      * `"application_domain"`: スペクトルインデックスのアプリケーションドメインまたは使用ケース。
      * `"reference"`: スペクトルインデックスの公式の参照または出典。
      * `"formula"`: スペクトルインデックスの数学的公式。
      * `"date_of_addition"`: スペクトルインデックスが追加された日付（"yyyy-mm-dd"形式）。
      * `"contributor"`: スペクトルインデックス情報の寄稿者または出典。
      * `"platforms"`: インデックスが適用されるプラットフォームまたはセンサー。

# 戻り値

指定されたインデックス情報を含む `SpectralIndex` オブジェクト。

# 例

```julia-repl
julia> indices["NIRv"]

```

または、提供されたスペクトルインデックスの辞書に直接アクセスする：

```julia-repl
NIRv
```
