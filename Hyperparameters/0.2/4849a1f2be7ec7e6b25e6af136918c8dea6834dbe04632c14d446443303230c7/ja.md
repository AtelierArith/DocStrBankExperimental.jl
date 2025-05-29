```
report_hyperparameters(save_dir::AbstractPath; prefix="SM_HP_")
```

すべてのハイパーパラメータを `save_dir` にある "hyperparameters.json" という名前のJSONファイルに保存し、各キーと値のペアをロガーに出力します。

ハイパーパラメータは、使用されたすべてのハイパーパラメータのキャッシュされた `HYPERPARAMETERS` 辞書から取得され、プレフィックスに一致する環境変数と組み合わされます。両方に存在する場合は、キャッシュされた辞書が優先されます。環境変数から読み取られたハイパーパラメータはすべて文字列として記録されます。（これを上書きするには、レポートの前に `hyperparam(type, name)` を使用します）

コンポーネントを抽出するための正規表現は次のとおりです: `hyperparameters: (?<key>)=(?<value>)`。
