```
communication_classes(x)
```

# 定義

状態 $j$ は状態 $i$ からアクセス可能であるとは、プロセスが状態 $i$ から始まった場合に最終的に状態 $j$ に到達することが可能であることを意味します。すなわち、$∃ \, t ∈ \mathbb{N}$ で $p^{(t)}_{i,j} > 0$ です。

状態 $i$ と $j$ は、$i$ が $j$ からアクセス可能であり、$j$ が $i$ からアクセス可能である場合に通信していると言います。

通信クラスは、マルコフ連鎖の中で互いにアクセス可能な状態の集合です。通信クラスは数学的な意味でのクラスを形成します。また、状態空間の分割を形成します。

状態 $i$ は再帰的であるとは、プロセスが状態 $i$ から始まった場合に最終的に状態 $i$ に戻ることが保証されていることを意味します。状態 $i$ が再帰的でない場合、それは一時的であると言います。

# 引数

  * `x`: 何らかのマルコフ連鎖。

# 戻り値

2つの配列を含むタプル。

  * 最初の配列は、通信する状態を格納するC配列を含みます。
  * 2番目の配列はBoolの配列で、i番目の値が真であればi番目の通信クラスが再帰的であることを示します。

# 例

```jldoctest communication_classes
using DiscreteMarkovChains
T = [
    1 0;
    0 1;
]
X = DiscreteMarkovChain(T)

communication_classes(X)

# 出力

([[1], [2]], Any[true, true])
```

したがって、マルコフ連鎖には2つの通信クラスがあり、どちらも再帰的です。

```jldoctest communication_classes
T = [
    .5 .5 .0;
    .2 .8 .0;
    .1 .2 .7;
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)

communication_classes(X)

# 出力

([["Sunny", "Cloudy"], ["Rainy"]], Any[true, false])
```

したがって、SunnyとCloudyの状態は通信しており、再帰的です。Rainyの状態は一時的です。雨が止んでしまうと、再び雨が降ることはないため、これはあまり良い天気モデルではないことに注意してください。
