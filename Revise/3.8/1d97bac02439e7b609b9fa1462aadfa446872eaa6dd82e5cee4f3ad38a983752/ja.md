Revise.jlはソースコードの変更を追跡し、実行中のJuliaセッションに変更を組み込みます。

Revise.jlは裏で動作します。パッケージを追跡するには、例えば`Example`を使用します：

```julia
(@v1.6) pkg> dev Example        # パッケージの開発コピーを作成
[...パッケージ出力省略...]

julia> using Revise             # これは開発中のパッケージの前に来る必要があります

julia> using Example

[...パッケージを開発...]     # Revise.jlはコードの変更に合わせてパッケージの機能を自動的に更新します

```

特別な状況で役立つRevise.jlの関数：

  * `Revise.track`: `Base` Julia自体または`Core.Compiler`の更新を追跡
  * `includet`: ファイルを読み込み、将来の変更を追跡。小さく迅速な作業向け
  * `entr`: コードが更新されるたびに追加の関数を呼び出す
  * `revise`: `Revise.revision_queue`の変更やモジュール内のすべての定義を評価
  * `Revise.retry`: 以前に失敗した修正を実行。順序依存のエラーの場合に便利
  * `Revise.errors`: `Revise.queue_errors`に表されるエラーを報告
