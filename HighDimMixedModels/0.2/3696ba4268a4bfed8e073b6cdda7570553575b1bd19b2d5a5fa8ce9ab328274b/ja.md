```
制御
```

座標降下アルゴリズムのハイパーパラメータ

# フィールド

  * `tol`: 小さな正の数、デフォルトは1e-4、収束許容度を提供
  * `seed`: ランダムシード、デフォルト770。アルゴリズムの唯一のランダム性は、固定効果パラメータの初期化時（交差検証のデータ分割のため）にあります
  * `trace`: Bool、デフォルトは`false`。`true`の場合、アルゴリズムの過程でコストとアクティブセットのサイズを印刷します。
  * `max_iter`: 整数、デフォルト1000、座標勾配降下の最大反復回数を指定します。
  * `max_armijo`: 整数、デフォルト20、Armijoアルゴリズムの最大ステップ数を指定します。最大に達した場合、アルゴリズムは現在の座標を更新せず、次の座標に進みます
  * `act_num`: 整数、デフォルト5。固定効果パラメータは`act_num`反復ごとにのみすべて更新します。それ以外の場合、現在のアクティブセットのパラメータのみを更新します。
  * `a₀`: Armijoステップのa₀、デフォルト1.0。このフィールドと次の5つのフィールドに関する詳細はSchelldorfer et al. (2010)を参照してください。
  * `δ`: Armijoステップのδ、デフォルト0.1。
  * `ρ`: Armijoステップのρ、デフォルト0.001。
  * `γ`: Armijoステップのγ、デフォルト0.0。
  * `lower`: ヘッセ行列の下限、デフォルト1e-6。
  * `upper`: ヘッセ行列の上限、デフォルト1e8。
  * `var_int`: Lの対角エントリを更新する際に最適化する区間の境界を持つタプル、デフォルトは(0, 100)。最適化のセクション「制約付き区間での単変数関数の最小化」を参照してください
  * `cov_int`: Lの非対角エントリを更新する際に最適化する区間の境界を持つタプル、デフォルトは(-50, 50)。最適化のセクション「制約付き区間での単変数関数の最小化」を参照してください
  * `optimize_method`: 単変数最適化を実行するためのメソッドを示すシンボル、:Brentまたは:GoldenSectionのいずれか、デフォルトは:Brent
  * `thres`: Lの対角エントリの更新が`thres`より小さい場合、パラメータは0に設定されます
