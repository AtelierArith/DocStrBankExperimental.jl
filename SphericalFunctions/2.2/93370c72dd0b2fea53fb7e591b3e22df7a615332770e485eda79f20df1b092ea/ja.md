```
complex_powers(z, m)
```

整数の冪 `z` を `z^0` から `z^m` まで再帰的に計算します。

`z` は正規化されており、複素振幅はおおよそ 1 であると仮定されています。

このアルゴリズムは主に Stoer と Bulirsch の「数値解析入門」（24ページ）に由来しており、de Moivre の公式、すなわち exp(iθ)ⁿ = exp(inθ) の助けを借りており、さらに異なる象限での異なる挙動に対処するための私自身の変更が加えられています。

この特殊な関数を使用することには通常大きな利点はありません。特定の冪が必要な場合、exp(iθ)ⁿ または exp(inθ) を明示的に計算する方が、一般的にははるかに効率的で同じくらい正確です。しかし、0 から m までのすべての冪が必要な場合、この関数は大きな m に対してそれらのオプションよりも約 10 倍または 5 倍速くなります。これらのオプションと同様に、この関数は数値的に安定しており、その誤差は通常、入力引数の機械精度誤差の m 倍よりも小さく、最悪でも約 50% 大きくなることがあります。これは位相が π/2 の倍数に近づくときに発生します。

参照: [`complex_powers!`](@ref) ```
