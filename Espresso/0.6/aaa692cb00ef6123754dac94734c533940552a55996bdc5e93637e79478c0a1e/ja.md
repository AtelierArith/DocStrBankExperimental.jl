簡略化ルールを追加するためのマクロ。例：

```
@simple_rule (-x * -y) (x * y)
```

ここで `(-x * -y)` は式にマッチするパターンであり、`(x * y)` は変換されるべきものです（式の書き換えを理解するために `rewrite()` を参照してください）。新しいルールを定義する際には、シンボル Set([:a, :b, :y, :x]) をプレースホルダーとして使用できます。他のすべてのシンボルは文字通りに解釈されます。
