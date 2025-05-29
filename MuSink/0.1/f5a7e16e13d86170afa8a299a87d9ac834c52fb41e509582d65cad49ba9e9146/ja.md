```
Workspace(problem::Problem; <keyword arguments>)
```

`problem`を解決するためのワークスペースを作成します。これは[`step!`](@ref)または[`converge!`](@ref)を呼び出すことで行えます。

すべてのオプション引数`arg`は、構築後に`set_[arg]!(ws, ...)`を介して設定することもできます。

## 引数

  * `eps = 1`。Sinkhornスケーリングパラメータ。
  * `rho = Inf`。周辺ペナルティパラメータ`rho`のデフォルト値。
  * `rhos`。ノードを`rho`値にマッピングする辞書。
  * `weights`。エッジをコストを重み付けする値にマッピングする辞書。
  * `reach = Inf`。到達パラメータ（最大許容輸送の半径）。
  * `logdomain = true`。ログまたは指数ドメインで作業するかどうか。
  * `stepmode = :stable`。潜在的な更新の順序を決定する戦略。詳細については[`Workspace`](@ref)のドキュメントを参照してください。
  * `atype = :array64`。バックエンドで使用される配列タイプ。
