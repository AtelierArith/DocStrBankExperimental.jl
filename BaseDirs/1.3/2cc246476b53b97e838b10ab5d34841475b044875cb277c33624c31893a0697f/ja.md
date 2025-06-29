**STATE_HOME** (`XDG_STATE_HOME`)

ユーザー固有の状態データが書き込まれるべき単一のベースディレクトリ。

これは、（アプリケーションの）再起動間で持続すべき状態データを含むべきですが、ユーザーにとって重要またはポータブルすぎるために `DATA_HOME` に保存されるべきではありません。含まれる可能性があるもの：

  * アクションの履歴（ログ、履歴、最近使用したファイルなど）
  * 再起動時に再利用できるアプリケーションの現在の状態（ビュー、レイアウト、オープンファイル、元に戻す履歴など）

**デフォルト値**

|            Linux |                          MacOS |        Windows |
| ----------------:| ------------------------------:| --------------:|
| `~/.local/state` | `~/Library/ApplicationSupport` | `LocalAppData` |
