```
ignore_gradient(x) -> x
```

任意の計算において勾配を無視します。逆モードではChainRulesCore APIを使用します。順方向モードでは、単にゼロの双対を持つ新しい数を返します。
