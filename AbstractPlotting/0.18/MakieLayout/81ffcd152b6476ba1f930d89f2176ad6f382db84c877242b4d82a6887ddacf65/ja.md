```
reset_limits!(ax; xauto = true, yauto = true)
```

`ax.limits`の値に応じて軸の制限をリセットします。制限の2つのコンポーネントのいずれかがnothingの場合、その値は、`xauto`または`yauto`がそれぞれtrueであればtargetlimitsからコピーされるか、軸内のプロットから自動的に決定されます。コンポーネントのいずれかが2つの数のタプルである場合、それらは直接使用されます。
