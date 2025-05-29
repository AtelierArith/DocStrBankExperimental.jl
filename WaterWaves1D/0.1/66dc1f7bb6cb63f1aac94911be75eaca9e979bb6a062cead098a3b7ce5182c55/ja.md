```
relaxedGreenNaghdi(param;kwargs)
```

初期値問題を解くための `AbstractModel` 型のオブジェクトを定義します。これは、[N. Favrie and S. Gavrilyuk](https://doi.org/10.1088/1361-6544/aa712d) または [C. Escalante, M. Dumbser and M. Castro](https://doi.org/10.1016/j.jcp.2019.05.035) および [G. Richard](https://doi.org/10.1016/j.euromechflu.2021.05.011) によって提案されたリラックスしたグリーン-ナグディモデルに基づいています。

# 引数

`param` は `NamedTuple` 型であり、以下を含む必要があります。

  * 無次元パラメータ `ϵ`（非線形性）および `μ`（分散）;
  * リラクゼーションパラメータ `a`;
  * キーワード引数として `mesh` が提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `FG`: `true` の場合（デフォルトは `false`）、Favrie-Gavrilyuk モデルを計算し、それ以外の場合は Escalante-Dumbser-Castro モデルを計算します;
  * `id`: `∈{0,1,2}` で、初期データの準備レベルを表します（デフォルトは `1`）;
  * `mesh`: コレクションポイントのメッシュ。デフォルトでは `mesh = Mesh(param)` です;
  * `iterative`: `true` の場合は GMRES を通じて初期データを構築するための楕円問題を解き、`false` の場合は LU 分解を使用します（デフォルトは `true`）;
  * `precond`: `true` の場合は GMRES のための（左）前処理器を使用し（デフォルト）、提供された場合は `precond` を前処理器として選択します;
  * `gtol`: GMRES アルゴリズムの相対許容誤差（デフォルトは `1e-14`）;
  * `restart`: GMRES アルゴリズムの対応するオプション（デフォルトは `100`）;
  * `maxiter`: GMRES の対応するオプション（デフォルトは `nothing`）;
  * `ktol`: Krasny フィルターの許容誤差（デフォルトは `0`、すなわちフィルタリングなし）;
  * `dealias`: Orlicz ルール `1-dealias/(dealias+2)` によるディーリアス処理（デフォルトは `0`、すなわちディーリアス処理なし）;
  * `label`: 将来の参照のためのラベル（デフォルトは `FG==true` の場合は `"Favrie-Gavrilyuk"`、それ以外の場合は `"Escalante-Dumbser-Castro"`）;

# 戻り値

`solve!` を介して初期値問題を解くために必要な要素を生成します：

1. 明示的な時間積分ソルバーで呼び出される関数 `relaxedGreenNaghdi.f!`；
2. `(η,v)` の型 `InitialData` から計算を実行するための生データ行列を提供する関数 `relaxedGreenNaghdi.mapto`；
3. そのようなデータ行列から実ベクトルのタプル `(η,v,x)` を返す関数 `relaxedGreenNaghdi.mapfro`、ここで

```
- `η` はコレクションポイント `x` での表面変形の値です;
- `v` は `x` での速度ポテンシャルのトレースの導関数です;
```

4. さらに、データ行列から実ベクトルのタプル `(η,v,u,p,w)` を返す便利な関数 `relaxedGreenNaghdi.mapfrofull`、ここで

```
- `u` は層平均の水平速度に対応します。
- `p` はリラックスした（人工的な）層平均の非水静圧に対応します;
- `w` はリラックスした（人工的な）層平均の垂直速度に対応します。
```
