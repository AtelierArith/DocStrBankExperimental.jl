```
SaintVenant(param;kwargs)
```

初期値問題を解くための `AbstractModel` 型のオブジェクトを定義します。これはサン・ヴェナン（または浅水）モデルに関連しています。

# 引数

`param` は `NamedTuple` 型で、以下を含む必要があります。

  * 無次元パラメータ `ϵ`（非線形性）;
  * `mesh` がキーワード引数として提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `mesh`: コレクションポイントのメッシュ。デフォルトでは `mesh = Mesh(param)` です;
  * `ktol`: ローパス・クラスニー・フィルターの許容誤差（デフォルトは `0`、すなわちフィルタリングなし）;
  * `dealias`: `0` または `false` に設定するとデイリアシングなし（デフォルト）、`1` または `true` に設定すると標準の 3/2 オルリッツルール、その他の値はデイリアシングシンボルの最大傾きを追加的に設定します（`2/dealias` モデルに影響します）;
  * `label`: 将来の参照用のラベル（デフォルトは `"Saint-Venant"`）;

# 戻り値

`solve!` を介して初期値問題を解くために必要な要素を生成します：

1. 明示的な時間積分ソルバーで呼び出される関数 `SaintVenant.f!`；
2. `(η,v)` の型 `InitialData` から計算が実行される生データ行列を提供する関数 `SaintVenant.mapto`；
3. そのようなデータ行列から実ベクトルのタプル `(η,v,x)` を返す関数 `SaintVenant.mapfro`、ここで

      * `η` はコレクションポイント `x` での表面変形の値です;
      * `v` は `x` での速度ポテンシャルのトレースの導関数です。

```
