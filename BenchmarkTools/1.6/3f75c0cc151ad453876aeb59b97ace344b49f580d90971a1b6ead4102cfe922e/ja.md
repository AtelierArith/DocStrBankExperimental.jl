```
@bprofile expression [other parameters...]
```

プロファイリング中に `@benchmark` を実行します。これは次のように似ています。

```
@profile @benchmark expression [other parameters...]
```

ただし、プロファイリングは主な実行（コンパイルとチューニングの後）にのみ適用されます。実行前にプロファイルバッファはクリアされます。

プロファイル結果は `Profile.print(...)` で表示します。詳細については、Juliaマニュアルのプロファイリングセクションを参照してください。
