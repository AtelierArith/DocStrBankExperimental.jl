変数 `v` は `AbstractDataVariable` から派生した型である必要があり、少なくとも以下を実装する必要があります：

  * `Base.parent(v)`: 変数の親配列

オプション：

  * `times(v)`: 変数のタイムスタンプ
  * `units(v)`: 変数の単位
  * `meta(v)`: 変数のメタデータ
  * `name(v)`: 変数の名前
