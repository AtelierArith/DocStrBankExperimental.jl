```
WhithamBoussinesq(param;kwargs)
```

初期値問題を解くためのBoussinesq型モデルの`AbstractModel`型のオブジェクトを定義します。完全分散特性を持ちます。

# 引数

`param`は`NamedTuple`型で、以下を含む必要があります。

  * 無次元パラメータ`ϵ`（非線形性）と`μ`（分散）;
  * キーワード引数として`mesh`が提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `Boussinesq`: `true`の場合（デフォルトは`false`）、標準のBoussinesqシステムを計算します（`Boussinesq(param;kwargs)`を参照）;
  * モデルを決定するパラメータ`α`:

      * `α = 1`（デフォルト）の場合、モデルは[Dinvay, Dutykh and Kalisch](https://doi.org/10.1016/j.apnum.2018.09.016)で導入されています;
      * `α = 1/2`の場合、モデルは準線形バージョンです;
      * `α < 1/2`の場合、モデルの不適切性から生じる不安定性が予想されます。
  * `mesh`: コレクションポイントのメッシュ。デフォルトでは`mesh = Mesh(param)`です;
  * `ktol`: ローパスKrasnyフィルタの許容誤差（デフォルトは`0`、すなわちフィルタリングなし）;
  * `dealias`: Orliczルール`1-dealias/(dealias+2)`によるディーリアス処理（デフォルトは`0`、すなわちディーリアス処理なし）;
  * `label`: 将来の参照用のラベル（デフォルトは`"Whitham-Boussinesq"`）;

# 戻り値

`solve!`を介して初期値問題を解くために必要な要素を生成します：

1. 明示的時間積分ソルバーで呼び出される関数`WhithamBoussinesq.f!`;
2. `(η,v)`の型`InitialData`から計算が実行される生データ行列を提供する関数`WhithamBoussinesq.mapto`;
3. そのようなデータ行列から実ベクトルのタプル`(η,v,x)`を返す関数`WhithamBoussinesq.mapfro`、ここで

```
- `η`はコレクションポイント`x`での表面変形の値です;
- `v`は`x`での速度ポテンシャルのトレースの導関数です。
```
