```
isbounded(P::AbstractHPolygon, [use_type_assumption]::Bool=true)
```

制約表現における多角形が有界であるかどうかを判断します。

### 入力

  * `P`                   – 制約表現の多角形
  * `use_type_assumption` – （オプション、デフォルト: `true`）多角形が有界であるという型の仮定を無視するためのフラグ

### 出力

`use_type_assumption` が有効な場合は `true` を返します。それ以外の場合、`P` が有界であれば `true` を返します。

### アルゴリズム

`!use_type_assumption` の場合、[`_isbounded_unit_dimensions`](@ref) を使用します。
