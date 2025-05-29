```
SerreGreenNaghdi(param;kwargs)
```

初期値問題を解くための `AbstractModel` 型のオブジェクトを定義します。これは Serre-Green-Naghdi モデルに基づいています ([Serre](https://10.1051/lhb/1953058), [Su and Gardner](https://10.1063/1.1664873), [Green and Naghdi](https://10.1017/s0022112076002425))。

# 引数

`param` は `NamedTuple` 型で、以下を含む必要があります。

  * 無次元パラメータ `ϵ` (非線形性) と `μ` (分散);
  * キーワード引数として `mesh` が提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `mesh`: コレクションポイントのメッシュ。デフォルトでは `mesh = Mesh(param)` です;
  * `iterative`: `true` の場合は GMRES を通じて楕円問題を解決し、`false` の場合は LU 分解を使用します (デフォルトは `true`);
  * `precond`: `true` の場合は GMRES のための (左) 前処理器を使用し (デフォルト)、提供された場合は `precond` を前処理器として選択します;
  * `gtol`: GMRES アルゴリズムの相対許容誤差 (デフォルトは `1e-14`);
  * `restart`: GMRES アルゴリズムの対応するオプション (デフォルトは `100`);
  * `maxiter`: GMRES の対応するオプション (デフォルトは `nothing`);
  * `ktol`: Krasny フィルターの許容誤差 (デフォルトは `0`、すなわちフィルタリングなし);
  * `dealias`: Orlicz ルール `1-dealias/(dealias+2)` によるディーリアシング (デフォルトは `0`、すなわちディーリアシングなし);
  * `label`: 将来の参照のためのラベル (デフォルトは `"Green-Naghdi"`);

# 戻り値

`solve!` を通じて初期値問題を解くために必要な要素を生成します：

1. 明示的時間積分ソルバーで呼び出される関数 `SerreGreenNaghdi.f!`;
2. `(η,v)` の型 `InitialData` から計算が実行される生データ行列を提供する関数 `SerreGreenNaghdi.mapto`;
3. そのようなデータ行列から実ベクトルのタプル `(η,v,x)` を返す関数 `SerreGreenNaghdi.mapfro`、ここで

      * `η` はコレクションポイント `x` での表面変形の値です;
      * `v` は `x` での速度ポテンシャルのトレースの導関数です;
4. さらに、データ行列から実ベクトルのタプル `(η,v,u)` を返す便利な関数 `SerreGreenNaghdi.mapfrofull` もあり、ここで

      * `u` は層平均速度に対応します。

```
