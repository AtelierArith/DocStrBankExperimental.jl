```
reset_limits!(ax; xauto = true, yauto = true)
```

`ax.limits`の値に応じて軸の制限をリセットします。制限の2つのコンポーネントのうちの1つが`nothing`の場合、その値は、`xauto`または`yauto`がそれぞれ`true`の場合は`targetlimits`からコピーされるか、または軸内のプロットから自動的に決定されます。コンポーネントの1つが2つの数のタプルである場合、それらは直接使用されます。
