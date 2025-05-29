```
NonHydrostatic(param;kwargs)
```

`AbstractModel`型のオブジェクトを定義し、[Bristeau, Mangeney, Sainte-Marie and Seguin](https://doi.org/10.3934/dcdsb.2015.20.961)によって提案された「非水圧」モデルの初期値問題を解決します。

# 引数

`param`は`NamedTuple`型であり、以下を含む必要があります。

  * 無次元パラメータ`ϵ`（非線形性）および`μ`（分散）;
  * `mesh`がキーワード引数として提供されていない場合、コレクションポイントのメッシュを構築するための数値パラメータ。

## オプションのキーワード引数

  * `mesh`: コレクションポイントのメッシュ。デフォルトでは`mesh = Mesh(param)`です;
  * `iterative`: `true`の場合はGMRESを通じて楕円問題を解決し、`false`の場合はLU分解を使用します（デフォルトは`true`です）;
  * `precond`: `true`の場合はGMRESのための（左）前処理器を使用し（デフォルト）、提供された場合は`precond`を前処理器として選択します;
  * `gtol`: GMRESアルゴリズムの相対許容誤差（デフォルトは`1e-14`です）;
  * `restart`: GMRESアルゴリズムの対応オプション（デフォルトは`100`です）;
  * `maxiter`: GMRESの対応オプション（デフォルトは`nothing`です）;
  * `ktol`: Krasnyフィルターの許容誤差（デフォルトは`0`、すなわちフィルタリングなし）;
  * `dealias`: Orliczルール`1-dealias/(dealias+2)`によるディーリアス処理（デフォルトは`0`、すなわちディーリアス処理なし）;
  * `label`: 将来の参照のためのラベル（デフォルトは`"non-hydrostatic"`です）;

# 戻り値

`solve!`を介して初期値問題を解決するために必要な要素を生成します：

1. 明示的な時間積分ソルバーで呼び出される関数`NonHydrostatic.f!`;
2. `(η,v)`の型`InitialData`から計算が実行される生データ行列を提供する関数`NonHydrostatic.mapto`;
3. そのようなデータ行列から実ベクトルのタプル`(η,v,x)`を返す関数`NonHydrostatic.mapfro`、ここで

      * `η`はコレクションポイント`x`での表面変形の値です;
      * `v`は`x`での速度ポテンシャルのトレースの導関数です;
4. さらに、データ行列から実ベクトルのタプル`(η,v,u)`を返す便利な関数`NonHydrostatic.mapfrofull`、ここで

      * `u`は層平均速度に対応します。

```
