```
optimize_for_one_epoch!(opt, model, ps, dl, batch, loss, λY)
```

`dl`に含まれるデータを`batch`に従ってサンプリングし、これらのバッチに対して最適化を行います。

このステップでは、`loss`に対して自動微分も行います。

`optimize_for_one_epoch!`の出力は、エポックのすべてのバッチにわたる平均損失です：

$$
output = \frac{1}{\mathtt{steps\_per\_epoch}}\sum_{t=1}^\mathtt{steps\_per\_epoch}\mathtt{loss}(\theta^{(t-1)}).
$$

これは、任意の*逆微分*ルーチンには常に2つの出力があるためです；`Zygote`の場合：

```julia
loss_value, pullback = Zygote.pullback(ps -> loss(model, ps, input, output), ps)
```

したがって、ADを使用してプルバックを計算するたびに損失の値を無料で取得できます。

# 引数

すべての引数は必須です（デフォルトはありません）：

1. [`Optimizer`](@ref)のインスタンス。
2. ニューラルネットワークモデル。
3. ニューラルネットワークパラメータ`ps`。
4. データ（すなわち、[`DataLoader`](@ref)のインスタンス）。
5. `batch`::[`Batch`](@ref): `batch_size`（およびオプションで`seq_length`と`prediction_window`）を格納します。
6. `loss::NetworkLoss`。
7. パラメータ`ps`の*セクション* `λY`。

# 実装

内部的には、各ミニバッチに対して[`optimization_step!`](@ref)を呼び出します。

ミニバッチの数は[`number_of_batches`](@ref)で決定できます：

```jldoctest
using GeometricMachineLearning
using GeometricMachineLearning: number_of_batches

data = [1, 2, 3, 4, 5]
batch = Batch(2)
dl = DataLoader(data; suppress_info = true)

number_of_batches(dl, batch)

# output

3
```
