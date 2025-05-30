```
gkldiv(a, b)
```

2つの配列間の一般化クルバック・ライブラー発散を計算します：$\sum_{i=1}^n (a_i \log(a_i/b_i) - a_i + b_i)$。`sum(a*log(a/b)-a+b)`の効率的な同等物。
