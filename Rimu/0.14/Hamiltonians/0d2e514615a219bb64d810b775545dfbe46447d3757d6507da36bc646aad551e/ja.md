```
HOCartesianContactInteractions(addr; S, η, g = 1.0, interaction_only = false, block_by_level = true)
```

接触相互作用を持つ直交基底のボソニック調和振動子を実装します。

$$
\hat{H} = \sum_{i} \epsilon_\mathbf{i} n_\mathbf{i} + \frac{g}{2}\sum_\mathbf{ijkl}
    V_\mathbf{ijkl} a^†_\mathbf{i} a^†_\mathbf{j} a_\mathbf{k} a_\mathbf{l}.
$$

$$
D
$$

次元の調和振動子に対して、インデックス $\mathbf{i}, \mathbf{j}, \ldots$ は $D$-タプルです。エネルギースケールは最初の次元、すなわち $\hbar \omega_x$ によって定義され、単一粒子のエネルギーは次のようになります。

$$
    \frac{\epsilon_\mathbf{i}}{\hbar \omega_x} = (i_x + 1/2) + \eta_y (i_y+1/2) + \ldots.
$$

因子 $\eta_y, \ldots$ は異方的なトラッピング幾何学を可能にし、$\omega_x$ が最小のトラッピング周波数となるように `1` より大きいと仮定されます。

デフォルトでは、相互作用によるオフダイアゴナル要素は一次の縮退摂動理論と一致します。

$$
    V_{\mathbf{ijkl}} = \delta_{\epsilon_\mathbf{i} + \epsilon_\mathbf{j}}
        ^{\epsilon_\mathbf{k} + \epsilon_\mathbf{l}}
        \prod_{d \in x, y,\ldots} \mathcal{I}(i_d,j_d,k_d,l_d),
$$

ここで、$\delta$ 関数は *総* 非相互作用エネルギーが保存されることを示し、同じ非相互作用エネルギーを持つすべての状態がこの相互作用によって接続され、ハミルトニアンは非相互作用エネルギーレベルに従ってブロックされます。`block_by_level = false` を設定すると、この制限が無効になり、任意の非相互作用エネルギーレベルの基底状態間の結合が可能になり、オフダイアゴナルが増え、ブロックが少なくても大きくなります（ブロックは依然として基底状態のパリティによって区別されます）。別の方法として、空間次元ごとにエネルギーを別々に保存するより強い制限を持つモデルについては [`HOCartesianEnergyConservedPerDim`](@ref) を参照してください。積分 $\mathcal{I}(a,b,c,d)$ は四つの一次元調和振動子基底関数のもので、[`four_oscillator_integral_general`](@ref) に実装されています。

# 引数

  * `addr`: 開始アドレス、粒子の数とモードの総数を定義します。
  * `S`: 各次元のレベル数のタプル、基底状態を含みます。状態間の許可される結合は `S .- 1` のアスペクト比によって定義されます。デフォルトでは、`addr` のモードに一致するレベル数を持つ1Dスペクトルになります。最初の次元を最大にするためにソートされます。
  * `η`: トラッピングポテンシャルの強度のカスタムアスペクト比を定義します。これは `S .- 1` から導出するのではなく、単一粒子エネルギースケールにのみ影響し、相互作用には影響しません。値は常に最初の次元に対してスケーリングされ、システムのエネルギースケール $\hbar\omega_x$ を設定します。
  * `g`: （等方的な）ベア相互作用パラメータ。`g` の値はトラップ単位であると仮定されます。
  * `interaction_only`: `true` に設定すると、非相互作用の単一粒子項は無視されます。相互作用によるエネルギーシフトのみが必要な場合に便利です。
  * `block_by_level`: `false` に設定すると、相互作用が非相互作用エネルギーを比較せずにすべての状態を結合できるようになります。

!!! warning
    `num_offdiagonals` はこのハミルトニアンの悪い推定です。行列を構築したり、QMCメソッドを使用する際には注意してください。最初に [`get_all_blocks`](@ref) を使用し、その後 `col_hint = block_size` オプションを [`BasisSetRep`](@ref) に渡して安全に行列を構築してください。


```
