```
@ballocated expression [other parameters...]
```

Juliaに含まれる`@allocated`マクロと同様に、指定された式を実行したときに割り当てられたバイト数を返します。 ただし、`@benchmark`マクロを使用し、`@benchmark`と同じ追加パラメータをすべて受け入れます。 返される割り当ては、ベンチマーク中に測定された*最小*経過時間の試行に対応します。
