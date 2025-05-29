```
AbstractLocalModel
```

ローカルモデルを使用してクエリポイント `q` の予測を行うメソッドのスーパークラスであり、[1] のメソッドに従います。具体的なサブタイプは `AverageLocalModel` と `LinearLocalModel` です。

すべてのモデルは、選択した関数で近隣を重み付けし、遠くの近隣が予測に与える影響を小さくし、補間が滑らかになるようにします。私たちが使用するデフォルトの重み付け関数は次のとおりです。

$$
\begin{aligned}
ω_i(d_i,d_{max}) = \left[ 1- \left(\frac{d_i}{d_{max}}\right)^2\right]^4
\end{aligned}
$$

ここで、$d_i = ||x_{nn,i} -q||_2$ は各近隣のクエリポイントからの距離です。

独自の関数を提供することもできますし、エッジケースを考慮した安全なバージョンの $ω$ として `ω_safe(d, dmax) = dmax > 0 ? (1.1 - (d/dmax)^2)^4 : 1.0` を提供することもできます。最後に、`ω` の代わりに `nothing` を指定することもできます。その場合、重み付けは行われず、近隣の直接平均が返されます。

### 平均ローカルモデル

```
AverageLocalModel(ω)
```

予測は、クエリポイント `q` の近隣 $x_{nn, i}$ の画像 $y_{nn, i}$ の重み付き平均に過ぎず、与えられた関数 `ω` を使用して重み付けされます。

$$
\begin{aligned}
y_{pred} = \frac{\sum{\omega_i y_{nn,i}}}{\sum{\omega_i}}
\end{aligned}
$$

### 線形ローカルモデル

```
LinearLocalModel([ω ], μ::Real=2.)
LinearLocalModel([ω ], s_min::Real, s_max::Real)
```

予測は、クエリの近隣 $x_{nn, i}$ とその画像 $y_{nn,i}$ に対する重み付き線形回帰です。[1] に示されています。

`μ` または `s_min` と `s_max` のいずれかを指定することで、適用される正則化のタイプが決まります。

  * `μ` : リッジ回帰

    $$
    \begin{aligned}
    f(\sigma) = \frac{\sigma^2}{\mu^2 + \sigma^2}
    \end{aligned}
    $$
  * `s_min`, `s_max` : ソフトスレッショルド

    $$
    \begin{aligned}
    f(\sigma) = \begin{cases} 0, & \sigma < s_{min}\\
    \left(1 - \left( \frac{s_{max}-\sigma}{s_{max}-s_{min}}\right)^2 \right)^2,
    &s_{min} \leq \sigma \leq s_{max} \\
    1, & \sigma > s_{max}\end{cases}
    \end{aligned}
    $$

## 参考文献

[1] : D. Engster & U. Parlitz, *Handbook of Time Series Analysis* Ch. 1, VCH-Wiley (2006)
