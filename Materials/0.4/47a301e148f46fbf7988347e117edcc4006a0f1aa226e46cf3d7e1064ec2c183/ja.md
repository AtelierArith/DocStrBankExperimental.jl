```
integrate_material!(material::AbstractMaterial)
```

1つのタイムステップを統合します。入力の `material.variables` は古い問題の状態を表します。

抽象メソッドです。各材料タイプに対して実装する必要があります。統合が完了したら、メソッドは **必ず** 新しい状態を `material.variables_new` に書き込む必要があります。

`material.variables` に書き込んではいけません。実際にタイムステップを確定させる（すなわち、時間の進化の1ステップを受け入れ、それを永続的に適用すること）は `update_material!` の仕事です。
