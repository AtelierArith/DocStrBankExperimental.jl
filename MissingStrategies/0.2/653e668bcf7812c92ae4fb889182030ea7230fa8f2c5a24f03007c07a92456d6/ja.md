```
MissingStrategy()
```

欠損値の処理方法を示す抽象型およびシングルトン型のスーパタイプ

  * └`PassMissing`: シングルトン: 欠損値が見つかった場合は欠損を返す
  * └`HandleMissingStrategy`: 抽象型: 欠損値を意識的に考慮する

      * └`SkipMissing`: 欠損値を無視する
      * └`ExactMissing`: バイアスのない処理

これらの戦略を処理するメソッドによって関数を拡張する方法については、[`@handlemissings_typed`](@ref)を参照してください。  
