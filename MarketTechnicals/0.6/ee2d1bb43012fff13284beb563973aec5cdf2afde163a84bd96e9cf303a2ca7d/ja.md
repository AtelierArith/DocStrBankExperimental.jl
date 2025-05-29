```
awesomeoscillator(ohlc::TimeArray, s = 5, n = 34; h = :High, l = :Low)
```

オーサムオシレーター

オーサムオシレーターは、市場のモメンタムを測定するために使用される指標です。AOは、34期間と5期間の単純移動平均の差を計算します。使用される単純移動平均は、終値ではなく各バーの中間点を使用して計算されます。AOは一般的にトレンドを確認したり、可能な反転を予測するために使用されます[1]。

オーサムオシレーターは、バーの中央点 (H+L)/2 を通してプロットされた34期間の単純移動平均であり、バーの中央点を横断する5期間の単純移動平均から引かれます $\frac{H + L}{2}$ [2]。

$$
\begin{align*}
  \text{中央値価格} & = \frac{P^\text{High} + P^\text{Low}}{2} \\
  \text{AO}           & = \text{SMA}(\text{中央値価格}, 5) -
                          \text{SMA}(\text{中央値価格}, 34)
\end{align*}
$$

# 参考文献

1. [TradingView](https://www.tradingview.com/wiki/Awesome_Oscillator_(AO))
2. https://www.ifcm.co.uk/ntx-indicators/awesome-oscillator
