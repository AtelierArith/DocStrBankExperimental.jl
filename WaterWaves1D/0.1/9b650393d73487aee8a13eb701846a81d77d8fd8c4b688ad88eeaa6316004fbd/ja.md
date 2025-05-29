```
WhithamGreenNaghdi(param;kwargs)
```

[Duchêne, Israwi and Talhouk](https://doi.org/10.1137/130947064)によって提案された完全分散型グリーン-ナグディモデルの初期値問題を解くために、`AbstractModel`型のオブジェクトを定義します。

# 引数

`param`は`NamedTuple`型で、以下を含む必要があります。

  * 無次元パラメータ`ϵ`（非線形性）および`μ`（分散）；
  * キーワード引数として`mesh`が提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `SGN`: `true`の場合（デフォルトは`false`）、Whitham-Green-Naghdi（WGN）システムの代わりにSerre-Green-Naghdi（SGN）を計算します（`SerreGreenNaghdi(param;kwargs)`を参照）；
  * `mesh`: コレクションポイントのメッシュ。デフォルトでは`mesh = Mesh(param)`；
  * `iterative`: `true`の場合はGMRESを通じて楕円問題を解決し、`false`の場合はLU分解を使用します（デフォルトは`true`）；
  * `precond`: `true`の場合はGMRESのための（左）前処理器を使用し（デフォルト）、提供された場合は`precond`を前処理器として選択します；
  * `gtol`: GMRESアルゴリズムの相対許容誤差（デフォルトは`1e-14`）；
  * `restart`: GMRESアルゴリズムの対応するオプション（デフォルトは`100`）；
  * `maxiter`: GMRESの対応するオプション（デフォルトは`nothing`）；
  * `ktol`: Krasnyフィルターの許容誤差（デフォルトは`0`、すなわちフィルタリングなし）；
  * `dealias`: Orliczルール`1-dealias/(dealias+2)`によるディーリアス処理（デフォルトは`0`、すなわちディーリアス処理なし）；
  * `label`: 将来の参照のためのラベル（デフォルトは`"Whitham-Green-Naghdi"`）；

# 戻り値

`solve!`を介して初期値問題を解くために必要な要素を生成します：

1. 明示的時間積分ソルバーで呼び出される関数`WhithamGreenNaghdi.f!`；
2. `(η,v)`の型`InitialData`から計算を実行するための生データ行列を提供する関数`WhithamGreenNaghdi.mapto`；
3. そのようなデータ行列から実ベクトルのタプル`(η,v,x)`を返す関数`WhithamGreenNaghdi.mapfro`、ここで

```
- `η`はコレクションポイント`x`での表面変形の値；
- `v`は`x`での速度ポテンシャルのトレースの導関数；
```

4. さらに、データ行列から実ベクトルのタプル`(η,v,u)`を返す便利な関数`WhithamGreenNaghdi.mapfrofull`、ここで

      * `u`は層平均速度に対応します。

```
