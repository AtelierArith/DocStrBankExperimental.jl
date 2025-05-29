```
gelu_erf(x) = xΦ(x) = 0.5x * (1 + erf(x/√2))
```

["ガウス誤差線形ユニット"](https://arxiv.org/abs/1606.08415)からの近似なしの活性化関数。この関数を使用するには、SpecialFunctions.jlパッケージをロードする必要があります。
