`MangalNetwork`は*ノード*をラップするものであり、相互作用をラップするものではありません。これはここで言及する価値のある理由ではありませんが、いくつかのヒントについては`MangalNode`のドキュメントを参照してください。

`name` (`AbstractString`): ネットワークを説明するユニークな名前。

`dataset` (`Int64`): ネットワークが属する`MangalDataset`のユニークID。

`public` (`Bool`): ネットワークの詳細が所有者以外に利用可能かどうかを示します。

`date` (`DateTime`): ネットワークがサンプリングされた日時。

`position` (`AbstractGeometryTrait`): ネットワークがサンプリングされた位置。この位置は、ポイント*または*ポリゴンなど、あらゆる種類の地理空間構造である可能性があります。

`complete` (`Bool`): ネットワークが完全にサンプリングされたか、またはギャップのある相互作用のコレクションであるかを示します。

`reference` (`Union{Int64,Nothing}`) (*optional*): `MangalReference`の`id`への参照、またはこのネットワークに関連する参照がない場合は`nothing`。

`user` (`Int64`): データベースにネットワークを追加したユーザーの`id`。これは*必ずしも*ネットワークの著者ではありません。実際の著作権を得るには`reference`を参照してください。

`description` (`AbstractString`): ネットワークの自由形式の説明。
