```
apply(gate::StaticGate, pstr, coeff, theta)
```

`StaticGate`に対してapplyを呼び出すと、パラメータ`theta`なしの3引数apply関数にディスパッチされます。具体的な型に対して4引数apply関数が定義されている場合でも、それにディスパッチされます。カスタムゲートを定義する方法の例については、`4-custom-gates.ipynb`を参照してください。
