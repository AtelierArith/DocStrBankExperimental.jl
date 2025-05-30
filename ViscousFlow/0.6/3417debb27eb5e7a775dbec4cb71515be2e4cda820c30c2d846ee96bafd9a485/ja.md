```
viscousflow_system(grid,[bodies];kwargs...)
```

粘性流れの問題のための演算子とキャッシュ変数を構築します。

`kwargs` はオプションのキーワード引数です。いくつかの引数は特定のタイプの問題にとって重要です。

  * `ddftype =` DDFタイプを設定します。デフォルトは `CartesianGrids.Yang3` です。
  * `scaling =` スケーリングタイプを設定します。`GridScaling`（デフォルト）または `IndexScaling`。
  * `dtype =` 要素タイプを `Float64`（デフォルト）または `ComplexF64` に設定します。
  * `phys_params =` 物理パラメータを渡すための辞書、または「freestream」キーを使用して自由流速度の代替モデルを渡すための辞書。
  * `bc =` 境界条件データまたは関数を渡すための辞書で、「external」と「internal」キーを使用して、対応する表面データを外部および内部から提供する関数を渡します。
  * `forcing =` 強制モデルを渡すための辞書（「forcing models」キーを介して）。
  * `motions =` 没入した表面の速度を指定する関数を提供します。
  * `reference_body =` 問題を慣性フレームではなく、ボディに取り付けられた参照フレームで解決します（デフォルトはボディ番号0です）。
  * `timestep_func =` 時間依存の問題のために、時間ステップサイズを提供する関数を渡します。この関数は、`grid::PhysicalGrid` と `phys_params` の2つの引数を受け取り、時間ステップを返すことが期待されます。デフォルトは基本的なフーリエ/CFLタイプの関数 `default_timestep` です。

```
