```
AgentBasedModel
```

`AgentBasedModel`は、Agents.jlのモデルを包含する抽象スーパタイプです。すべてのモデルは`AgentBasedModel`の具体的な実装であり、そのインターフェースに従います（下記参照）。`ABM`は`AgentBasedModel`のエイリアスです。

## 利用可能な具体的実装

  * [`StandardABM`](@ref)
  * [`EventQueueABM`](@ref)

自分自身の`AgentBasedModel`のバージョンを作成するのも簡単です。詳細は[開発者ドキュメントの該当エントリ](@ref make_new_model)を参照してください。

## `AgentBasedModel`のインターフェース

  * `step!(model, args...)`はモデルを時間的に前進させます。
  * `model[id]`は指定された`id`を持つエージェントを返します。
  * `abmproperties(model)`はモデルレベルのプロパティを格納する`properties`コンテナを返します。
  * `model.property`: モデルの`properties`がキータイプ`Symbol`の辞書であるか、または複合型（`struct`）である場合、構文`model.property`はキー`:property`を持つモデルプロパティを返します。
  * `abmtime(model)`はモデルの現在の時間を返します。すべてのモデルは時間0から始まり、モデルが[`step!`](@ref)されると時間が増加します。
  * `abmrng(model)`はモデルの乱数生成器を返します。再現性を確立するために、すべての`rand`や類似の関数への呼び出しに`abmrng(model)`を使用することを強く推奨します。
  * `allids(model)/allagents(model)`はモデル内のすべてのID/エージェントに対するイテレータを返します。
  * `hasid(model, id)`はモデルに指定された`id`を持つエージェントが存在する場合に`true`を返します。

`AgentBasedModel`は、上記の構文と開発者ドキュメントに記載されているいくつかの追加関数から構成される拡張可能なインターフェースを定義します。このインターフェースに従うことで、新しいバリアントの`AgentBasedModel`を実装できます。このインターフェースにより、`AgentBasedModel`のインスタンスは任意の[API](@ref)で使用できます。たとえば、[`random_agent`](@ref)、[`move_agent!`](@ref)、または[`add_agent!`](@ref)のような関数は手動で実装する必要はなく、`AgentBasedModel`インターフェースに従っていればそのまま動作します。
