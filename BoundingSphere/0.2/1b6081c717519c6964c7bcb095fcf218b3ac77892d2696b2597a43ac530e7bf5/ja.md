```
WelzlMTF()
```

前方移動ヒューリスティックを用いたWelzlアルゴリズム。詳細は https://people.inf.ethz.ch/gaertner/subdir/texts/own*work/esa99*final.pdf のアルゴリズムIを参照してください。ほとんどの状況では、代わりに [`WelzlPivot`](@ref) を使用する方が良いです。

## 利点

  * 小さな例に対して高速

## 欠点

  * 数値安定性の問題に悩まされることがある
