```
@belapsed expression [other parameters...]
```

Juliaに含まれている`@elapsed`マクロに似ており、指定された式を実行するのにかかる経過時間（秒）を返します。ただし、`@benchmark`マクロを使用しており、`@benchmark`と同じ追加パラメータをすべて受け入れます。返される時間は、ベンチマーク中に測定された*最小*経過時間です。
