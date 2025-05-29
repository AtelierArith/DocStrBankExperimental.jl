`MangalDataset`は、単一の要素を含む可能性のあるネットワークのコレクションを特定します。データセットは、その`id`または`name`（どちらも*一意*です）によって識別されます。

`name` (`AbstractString`): データセットを説明する一意の名前。

`public` (`Bool`): データセットの詳細が所有者以外の他者に利用可能かどうかを示します。

`reference` (`Union{Int64,Nothing}`) (*オプション*): `MangalReference`の`id`への参照、またはこのデータセットに関連する参照がない場合は`nothing`。

`user` (`Int64`): データセットをデータベースに追加したユーザーの`id`。これは*必ずしも*データセットの著者ではありません。実際の著作権を取得するには、`reference`（および`MangalNetwork`の同じフィールド）を参照してください。

`description` (`AbstractString`): データセットの自由形式の説明。
