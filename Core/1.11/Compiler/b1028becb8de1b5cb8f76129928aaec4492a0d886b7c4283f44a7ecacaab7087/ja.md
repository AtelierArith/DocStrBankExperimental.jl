```
walk_to_defs(compact, val, typeconstraint, predecessors)
```

`val`から始めて、使用-定義チェーンをたどり、この`val`にフィードするすべての葉を取得します（パス条件によって除外された葉は剪定します）。

`predecessors(def, compact)`は、"phi-like"ノード（PhiNodeまたはCore.ifelse）の可能な前駆体のセットを返すコールバックであり、そうでない場合は`nothing`を返すべきです。
