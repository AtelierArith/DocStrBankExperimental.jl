```
clearsublevelalias!(I::Ion, sublevel)
```

Ion `I` の `sublevel` に対するエイリアスの割り当てを消去します。完全なサブレベル `Tuple{String,Real}` またはそのエイリアス `String` のいずれかを受け入れます。また、複数のエイリアス割り当てを一度の呼び出しで消去するために、サブレベルのベクターも受け入れます。
