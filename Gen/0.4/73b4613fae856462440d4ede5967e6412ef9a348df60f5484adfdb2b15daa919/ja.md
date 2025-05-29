```
(weight, retval) = assess(gen_fn::GenerativeFunction, args::Tuple, choices::ChoiceMap)
```

提案された割り当ての確率を返す

引数 $x$ (`args`) と割り当て $t$ (`choices`) が与えられたとき、$p(t; x) > 0$ であるならば、$r \sim q(\cdot; x, t)$ をサンプリングし、重み (`weight`) を返します：

$$
\log \frac{p(r, t; x)}{q(r; x, t)}
$$

$$
p(t; x) = 0
$$

の場合はエラーです。
