```
isbounded(P::HPolytope, [use_type_assumption]::Bool=true)
```

制約表現における多面体が有界であるかどうかを判断します。

### 入力

  * `P`                   – 制約表現における多面体
  * `use_type_assumption` – （オプション、デフォルト: `true`）多面体が有界であるという型の仮定を無視するためのフラグ

### 出力

`use_type_assumption` が有効な場合は `true` を返します。それ以外の場合は、`P` が有界である場合に限り `true` を返します。
