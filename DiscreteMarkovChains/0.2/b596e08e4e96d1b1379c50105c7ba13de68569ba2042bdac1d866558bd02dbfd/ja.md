```
is_absorbing(x)
```

# 定義

マルコフ連鎖は、少なくとも1つの吸収状態を持ち、すべての状態から吸収状態に到達可能であれば（必ずしも1ステップである必要はない）、吸収的である。

# 引数

  * `x`: ある種のマルコフ連鎖。

# 戻り値

マルコフ連鎖 `x` が吸収連鎖であれば `true` を返す。したがって、プロセスは最終的に吸収されることが保証されている。

# 例

以下は、吸収連鎖の典型的な例である。

```jldoctest is_absorbing
using DiscreteMarkovChains
T = [
    1.0 0.0 0.0;
    0.1 0.8 0.1;
    0.0 0.3 0.7;
]
X = DiscreteMarkovChain(T)

is_absorbing(X)

# output

true
```

マルコフ連鎖に吸収状態がない場合、その連鎖は吸収的ではない。逆は必ずしも真ではないことがすぐにわかる。

```jldoctest is_absorbing
T = [
    0.5 0.5 0.0;
    0.5 0.0 0.5;
    0.0 0.5 0.5;
]
X = DiscreteMarkovChain(T)

is_absorbing(X)

# output

false
```

以下のように、連鎖には複数の吸収状態があるが、プロセスがそれらの状態に吸収されることは保証されていない。

```jldoctest is_absorbing
T = [
    1 0 0 0;
    0 1 0 0;
    0 0 0 1;
    0 0 1 0;
]
X = DiscreteMarkovChain(T)

is_absorbing(X)

# output

false
```

# 参考文献

1. [ダートマス大学](https://www.dartmouth.edu/~chance/teaching_aids/books_articles/probability_book/Chapter11.pdf)
