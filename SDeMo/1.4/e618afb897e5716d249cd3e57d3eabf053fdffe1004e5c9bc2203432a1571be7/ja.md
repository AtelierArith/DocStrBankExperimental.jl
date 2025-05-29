```
f1(M::ConfusionMatrix)
```

F₁スコアは、適合率と再現率の調和平均として定義されます：

$$
2\times\frac{PPV\times TPR}{PPV + TPR}
$$

これは、内部でより一般的な`fscore`を使用します。
