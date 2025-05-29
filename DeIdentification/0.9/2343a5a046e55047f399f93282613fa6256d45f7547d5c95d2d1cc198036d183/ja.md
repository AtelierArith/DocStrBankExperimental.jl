```
deidentify(cfg::ProjectConfig)
```

これは `DeIdentified` 構造体のコンストラクタです。この型を使用して、`DeIdDataFrame` 変数の配列を格納し、`DeIdDataFrame` 間で共通の `salt_dict` と `dateshift_dict` を保持します。`salt_dict` は、どのクリアテキストにどの塩が使用されたかを追跡することを可能にします。これは再識別を行う場合にのみ必要です。`id_dict` 引数は、元の主要 ID のハッシュダイジェストと新しい研究 ID の辞書です。
