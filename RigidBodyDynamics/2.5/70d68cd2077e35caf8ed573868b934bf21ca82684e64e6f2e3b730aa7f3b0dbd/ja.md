```julia
submechanism(mechanism, submechanismroot; bodymap, jointmap)

```

`mechanism`の`submechanismroot`を根とする部分木から新しい`Mechanism`を作成します。

`mechanism`内の非木構造のジョイントは、後続と前の両方が部分木の一部である場合にのみ、返される`Mechanism`に表示されます。

キーワード引数:

  * `bodymap::AbstractDict{RigidBody{T}, RigidBody{T}}`: 入力メカニズムのボディから出力メカニズムのボディへのマッピングで埋められます
  * `jointmap::AbstractDict{<:Joint{T}, <:Joint{T}}`: 入力メカニズムのジョイントから出力メカニズムのジョイントへのマッピングで埋められます

ここで、`T`は`mechanism`の要素型です。
