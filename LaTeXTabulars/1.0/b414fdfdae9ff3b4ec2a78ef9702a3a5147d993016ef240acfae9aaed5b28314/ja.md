```julia
Rule()
Rule(kind)

```

水平ルール。ルールの`kind`はシンボルで指定され、一般的には`booktabs`のルールに対して`\KINDrule`として印刷されます。例えば、`Rule(:top)`は`\toprule`を印刷します。`\hline`を取得するには、`Rule{:h}`を使用します。
