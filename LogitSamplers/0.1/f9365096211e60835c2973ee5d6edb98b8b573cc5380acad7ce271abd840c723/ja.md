```
logitsample([rng], logits, [buffer=similar(logits)]) -> Int
```

Gumbel argmaxトリックを使用して、ロジット分布からインデックスをサンプリングします。

代わりにバッファを渡すことで、ランダム数を生成する際に新しい配列を割り当てるのを避けることができます。
