```
ExplicitAlgorithm(tableau, [constraint])
ExplicitAlgorithm(name, [constraint])
```

常微分方程を解くための明示的アルゴリズムを構築します。オプションで名前と制約を指定できます。最初のコンストラクタは任意の `ExplicitTableau` とオプションの制約を受け入れ、アルゴリズムに名前を付けません。2番目のコンストラクタは、アルゴリズム名からタブローとデフォルトの制約を自動的に決定します。この名前は `ERKAlgorithmName` でなければなりません。

`ExplicitAlgorithm` を使用することは、同じタブローを持つ `IMEXAlgorithm` を明示的および暗黙的傾向に対して使用するための単なるショートハンドであることに注意してください（およびニュートン法なしで）。
