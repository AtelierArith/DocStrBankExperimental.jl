```
Matsuno(param;kwargs)
```

初期値問題を解くための `AbstractModel` 型のオブジェクトを定義します。これは [Matsuno](https://doi.org/10.1103/PhysRevLett.69.609) によって提案された二次元深水モデルに基づいています。

# 引数

`param` は `NamedTuple` 型で、以下を含む必要があります。

  * 無次元パラメータ `ϵ`（非線形性）および `μ`（分散）;
  * オプションで、浅水/深水スケーリングファクター `ν`。デフォルトでは、`μ≦1` の場合は `ν=1`、それ以外の場合は `ν=1/√μ` です。`ν=0` または `μ=Inf` の場合は無限層ケースを設定します。
  * キーワード引数として `mesh` が提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `IL`: `IL=true`（または `μ=Inf`、または `ν=0`）の場合は無限層ケースを設定します。この場合、`ϵ` は傾斜パラメータです。デフォルトは `false` です。
  * `mesh`: コレクションポイントのメッシュ。デフォルトでは `mesh = Mesh(param)` です;
  * `dealias`: `true` の場合は `1/3` Orlicz ルールでのディーリアシング、`false` の場合はディーリアシングなし（デフォルト）;
  * `label`: 将来の参照用のラベル（デフォルトは `"Matsuno"`）;

# 戻り値

`solve!` を介して初期値問題を解くために必要な要素を生成します：

1. 明示的時間積分ソルバーで呼び出される関数 `Matsuno.f!`；
2. `(η,v)` の型 `InitialData` から計算を実行するための生データ行列を提供する関数 `Matsuno.mapto`；
3. そのようなデータ行列から実ベクトルのタプル `(η,v,x)` を返す関数 `Matsuno.mapfro`、ここで

      * `η` はコレクションポイント `x` での表面変形の値です；
      * `v` は `x` での速度ポテンシャルのトレースの導関数です。

```
