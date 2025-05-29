```
GL(; alpha=2.0)
```

損失報告反復アルゴリズムのための早期停止基準。

(再スケーリングされた)一般化損失が閾値`alpha`を超えると停止がトリガーされます。

**用語。** $E_1, E_2, ..., E_t$を損失のシーケンスとします。これは、例えば、いくつかの反復機械学習アルゴリズムに関連する損失のサンプル外推定です。すると、時刻`t`における*一般化損失*は次のように与えられます。

$$
GL_t = 100 (E_t - E_{opt}) \over |E_{opt}|
$$

ここで、$E_{opt}$はシーケンスの最小値です。

参考文献: [Prechelt, Lutz (1998): "Early Stopping- But When?", in *Neural Networks: Tricks of the Trade*, ed. G. Orr, Springer.](https://link.springer.com/chapter/10.1007%2F3-540-49430-8_3).
